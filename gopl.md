# 结构化与项目管理
- go的包管理基于路径，调用时使用包名
- go中通过设置`go env GO111MODULE=off/on/auto`来控制是否开启包管理，当auto且项目根目录有.mod文件时启用包管理
- 开启包管理后，在创建项目之初，需要在项目的根目录下首先使用`go mod init \<project_dir_name\>`， 之后在项目开发过程中，通过`go mod tidy`自动补全包管理文件
- 使用包管理后，.mod文件的内容类似java中的maven中的内容，负责处理项目来的包
- 在vscode中编写go时， 如果开启了包管理，建议使用language server，否则建议关闭

# 复合数据结构
## 数组
- 数组的长度定长
- 数组长度是数组类型的一部分，`[5]int`和`[10]int`属于不同的类型
- 如果想让数组元素为任意类型，可以使用空接口`interface{}`作为类型，但是在使用时必须先做类型判断
- 数组的声明和使用方式
```golang
var arr1 = [5]int{1, 2, 3, 4}
var arrLazy = [...]int{1, 2} // 数组大小由初始化决定
var arrName = [5]string{3: "Chris", 4:"Ros"} // 指定索引的初始化 {"", "", "","Chris", "Ros"}
var arrRoom = [20]int
var arrP = new([10]int)
```
- 注意，和c++的区别，数组在go中是值类型，也可以通过`new()`生成对应类型的对象的指针。`var arr1 = [5]int`是一个对象，`var arr2 = new([5]int)`得到的是一个`[5]int`类型对象的指针
- 在函数的参数传递时，直接把数组作为参数，特别是在大数组时，会消耗大量内存（值传递），此时有两种选择：
  - 传递指针
  - 传递切片（常用）

## 切片
- 切片是对底层数组的一个连续片段的底层类型（该数组称为相关数组，当不基于数组创建切片时，这个数组是匿名的）
- 切片的类型表示其元素类型的所有数组切片的集合
- 未初始化的切片值为nil
- 切片有两个值，分别是`len()`长度和`cap()`容量，类似动态数组的底层数组大小的概念，但是对切片的下标不能超过长度
- 切片的声明与初始化：
```golang
var s1 []type = arr[start:end]
var s2 []int = {1, 3, 5, 7}
var s3 []type = make([]type, len, cap)
```
- 可以从数组或切片生成一个新的切片，使用`a[low:high:max]`的方式声明， max-low的结果为容量，high-low的结果为长度。如果a是数组，max最大不能超过数组的长度，如果a是切片，max最大不超过切片的容量

切片的reslice（切片重组）

- 从一个切片获得一个新的长度的切片的过程称为切片重组
- 切片重组后，新老切片指向同一个底层数组
- 如果需要切断这种引用，尤其是需要发布的数据（方法返回值，无法对返回值的使用），可以使用`copy()`函数创建新的数组进行复制
- 向切片末尾追加数据时， 使用`append()`函数，当切片的容量不够时，该函数会创建新的切片返回，注意此时前后切片的相关数组已经发生了变化
- 对一个未初始化的切片使用`append`函数是无害的
- 有没有生成新的切片需要看原有切片的容量是否足够
- 关于切片重组是否会影响到原有切片，例子如下：
```golang
	s1 := []int{1, 2, 3, 4}
	s2 := s1[0:2:4]
	fmt.Println(s2)
	s2 = append(s2, 10)
	fmt.Println("修改了s1")
	fmt.Println(s2)
	fmt.Println(s1)
	s2 = append(s2, 11) // 修改了s1
	fmt.Println("修改了s1")
	fmt.Println(s2)
	fmt.Println(s1)
	s2 = append(s2, 12) //
	fmt.Println("创建了新的切片")
	fmt.Println(s2)
	fmt.Println(s1)
	s2[2] = 0
	fmt.Println("此时修改s2，s1不变化")
	fmt.Println(s2)
    fmt.Println(s1)
/*
output:
[1 2]
修改了s1
[1 2 10]
[1 2 10 4]
修改了s1
[1 2 10 11]
[1 2 10 11]
创建了新的切片
[1 2 10 11 12]
[1 2 10 11]
此时修改s2，s1不变化
[1 2 0 11 12]
[1 2 10 11]
*/
```
## 字典

- 字典是引用类型， 未初始化时为nil
- 字典的声明和初始化
```golang
var map1 map[keytype]valuetype
var map1 = make(map[keytype]valuetype)
var map2 = make(map[keytype]valuetype, 100) // 给定初始容量
```
- key的允许类型：任意可以用==或!=比较的类型， 例如string, int, float, 所有的数组，函数，字典，切片和结构体不能作为key（如果结构体中不包含数组切片，只包含内建类型是可以的）, 指针和接口类型也可以
- value可以是任意类型，也可以是空接口类型
- 删除字典中的键值使用`delete(map, key)`函数，如果key不存在不会报错

## range
- range语句中生成的值是真实集合元素的副本，操作这些值不会改变元数据
```golang
a := [5]int{1, 2, 3, 4, 5}
for i, v := range a {
    v *= 10 // 不改变原数组的内容
    a[i] *= 10 // 可以改变原数据
}
```