# pta summary
## tips
- (p7) 熟悉int的范围, 在10^9范围.
- (p8) float的有效精度在6-7位, double的有效精度在15-16位.
- (15) 取模运算的优先级和除法运算相同
- (p21) 对于double类型的变量, 其输出格式变成了%f, 但其在scanf中却是%lf
- (p33) 每个case语句都不需要使用大括号扩起来, 因为case本身默认两个case之间的内容全部属于上一个case的内容.
- (p39) 数组大小必须是常量, 可以是硬写的数值, 也可以是 const int 变量
- (p40) 一维数组的初始化, 在大括号内用都好隔开, 后面未被赋初值的元素将是随机值
- (p44) 二维数组的初始化, 如果部分元素没有被赋初值,将被初始化为0.
- (p45) 如果数组的大小较大(大概10^6级别) 需要将其定义在主函数外, 否则会使程序异常退出, 原因是函数内部申请的局部变量来自系统栈, 语序申请的空间较小, 而函数外部申请的全局变量来自静态存储区, 允许申请的空间较大.
- (p46) **memset和fill函数** memset(数组名, 值, sizeof(数组名)) 只用于赋值-1和0, 按字节赋值.,对数组赋其他值采用fill函数.【在c++11中有一种新的写法, 在申明后,使用一个空的初始化列表, 可以将所有元素初始化为0】
- (p49) gets在pta中禁止使用, 可以使用cin的getline或者fget()函数
- strcmp()函数用于比较两个字符串, 在cstring中.
- strcat() 可以将c风格的两个字符串进行连接.
- (p53) sscanf 和 sprintf, 两者的语法和scanf与printf类似, 但是多了一个参数 sscanf(位置, %format, var); 从位置读变量, 位置可以是字符串.sprintf(位置, %format, var) 将字符串写到位置, 位置可以是变量.
- p(75) 浮点数的比较中注意尽可能避免使用等号.
- scanf 和 printf的效率比cin和cout对象高, 这一点在平时不容易看出来, 但是在循环10^5的级别上, cout和cin会超时, 但是scanf和printf不会, 从这一点来说, 以后应该尽量使用p和s
- pat中的long int 和 int的长度相同, 当题目中说在long int范围内的时候, 需要尝试下long long int范围, 注意输入输出的时候的控制符也需要相应修改, 例题 `A1088`
## 列表初始化
构造结构时, 最好写一个默认构造函数, 初始化使用列表初始化
```cpp
playerNode() :arrive(""), serve(maxServe), playTime(0), waitTime(0), isVip(false){};
```
即使是int这样类型的数据, 也可以和建议通过列表初始化去初始化保证安全.
## 简单模拟
- [x] A1042
- [x] A1046
- [x] A1065
- [x] A1002
- [x] A1009
### 图形输出
- [x] A1031
### 进制转换
熟悉掌握进制转换的string方法和int方法
原理:
十进制数转其他进制: 对基取模,再除基, 得到由低到高的其他进制数
十进制转其他进制模板:
```cpp
vector<int> dec2a(int dec, int base)
{
    vector<int> result;
    do {
        result.push_back(dec % base);
        dec /= base; // 除的动作其实是减掉余数, 在提升base的exp
    }while(dec > 0);
    return result;
}
```
其他进制转十进制: 从右到左乘以一次基, 然后加上数本身
其他进制转十进制模板
```cpp
int base2dec(int num, int base) {
    int sum = 0;
    int product = 1;
    while (num != 0) {
        sum += (num % 10) * product;
        num /= 10;
        product *= base;
    }
    return sum;
}
```
对于超过10^9的要使用ll, 对于更大的要使用string. string的加法和乘法注意进位, 最高位的处理通常要仔细.
对应例题:
- [x] A1019
- [x] A1027
- [x] A1058
### 查找元素
- [x] A1011
- [x] A1006
- [x] A1036
### 字符串处理
- [x] A1061
- [x] A1073
- [x] A1001
- [x] A1005
- [x] A1035
- [x] A1077
- [x] A1082
字符呈现局部规律时, 可以通过双指针来操纵.
## 算法初步
### 排序问题
- [x] A1062
- [x] A1012
- [x] A1016
- [x] A1025
- [x] A1028
- [x] A1055
- [ ] A1075
- [ ] A1083
- [ ] A1080
- [ ] A1095
根据日期时间格式, 计算时间差的模板
```cpp
void count_minute(node n1, node n2, int &minute) {
     minute = 0;
    while (n1.day != n2.day || n1.hour != n2.hour || n1.minute != n2.minute) {
        n1.minute++;
        minute++;
        if (n1.minute == 60) {
            n1.hour++;
            n1.minute = 0;
        }
        if (n1.hour == 24) {
            n1.day++;
            n1.hour = 0;
        }
    }
}
```
### 二分查找与二分查找的扩展
一个标准版的二分查找模板
```cpp
int binsearch(int left, int right, int value) {
    while (left <= right) {
        int mid = (left + right) / 2;
        if (seq[mid] > value) {
            right = mid - 1;
        }
        else if (seq[mid] < value)
            left = mid + 1;
        else return mid;
    }
    return left; // 未找到, 返回value的插入位置
}
```
标准版的二分查找通常是为了找到一个准确值的位置, 其变化版本可以是找到相应条件的第一个或最后一个元素的位置, 作用类似与upper_bound和lower_bound
```cpp
int upper_bound(int left, int right, int val) { // 返回闭区间大于value的第一个
    while (left < right) { 
        int mid = (left + right) / 2;
        if (seq[mid] > val) right = mid;
        else left = mid + 1;
    }
    return left;
}
```
一个更加通用化的模板, 解决寻求满足有序序列中第一个满足某个条件的元素的位置的问题.
```cpp
int solve(int left, int right) {
    int mid;
    while (left < right) { // 对于[left, right]来说, left==right的情况
        mid = (left + right) / 2;
        if (条件成立) {
            right = mid;
        }
        else { // 条件不成立, 则第一个满足条件的位置大于mid
            left = mid ＋ 1;
        }
    }
    return left;
}
```

## 树算法
- [x] A1020
- [x] A1086
- [x] A1102
### 树的遍历和恢复
由前序遍历和中序遍历得到后序遍历的非递归非队列函数写法?
(待补充三个函数, 前序和中序得后序, 中序和后序得前序, 前序中序得层序)

前序和中序的序列求后序:
```cpp
void postorder(int root, int start, int end) { // root是pre序列的下标, start和end是in序列的下标
    if (start > end) return;
    int i = start;
    while (i < end && in[i] != pre[root]) i++;
    postorder(root + 1, start, i - 1);
    postorder(root + 1 + i - start, i + 1, end);
    post.push_back(pre[root]);
}
```

后序中序的序列求前序:
```cpp
void preorder(int  start, int end, int root_pos) {
    if (start > end) return ;
    pre.push_back(post[root_pos]);
    int i = start;
    while(in[i] != post[root_pos]) i++;
    preorder(start, i - 1, root_pos - (end - i) - 1);
    preorder(i + 1, end, root_pos - 1);
}
```
后序中序遍历的序列求层序遍历: (可以在求前序的基础上改)
```cpp
struct node {
    int index, value;
};
void preorder(int  start, int end, int root_pos, int index) {
    if (start > end) return ;
    pre.push_back({index, post[root_pos]});
    int i = start;
    while(in[i] != post[root_pos]) i++;
    preorder(start, i - 1, root_pos - (end - i) - 1, index * 2);
    preorder(i + 1, end, root_pos - 1, index * 2 + 1);
}
sort(pre.begin(), pre.end(), cmp);
bool cmp(node &n1, node &n2) {
    return n1.index < n2.index;
}
```
**遇到树的遍历问题, 关键在找到两个遍历 **

树的遍历
- [x] A1079
- [x] A1090
- [x] A1094
- [x] A1106
- [x] A1004

### 二叉搜索树
BST的定义是左边子树都小于, 右边都大于等于, 不要忽略了等遇到情况.
AVL树
AVL树是一种平衡二叉树, 实现的关键是四种旋转, 以及高度记录和高度更新.
四种旋转中, LL和RR都是基本旋转, 旋转后需要更新节点的高度, 而LR和RL都是LL和RR的组合, 可以直接按照字面意思, 先做下层旋转, 再做上层旋转. 
- 如何找到麻烦节点和发现节点?
每次插入节点后, 递归回程上检查高度是否满足, 若不满足, 当前不满足的便是发现点, 而麻烦点正是待插入的数据对应的点.
-  如何检查属于什么类型的旋转?
比较插入数据(麻烦点)和发现点的数据大小以及和发现点左儿子(右儿子)的数据的大小.
- 坑点?
insert结束前更新当前点高度, 检查旋转类型明确定义, 一侧是小于号则另一侧是大于等于.
```cpp
node* LL(node* root) { // 左左
    node *temp = root;
    root = root->left;
    temp->left = root->right;
    root->right = temp;
    temp->height = max(height(temp->right), height(temp->left)) + 1;
    root->height = max(height(root->left), height(root->right)) + 1;
    return root;
}
node* RR(node *root) { // 右右
    node *temp = root;
    root = root->right;
    temp->right = root->left;
    root->left = temp;
    temp->height = max(height(temp->right), height(temp->left)) + 1;
    root->height = max(height(root->left), height(root->right)) + 1;
    return root;
}
node* LR(node* root) { // 左右
    root->left = RR(root->left);
    return LL(root);
}
node* RL(node *root) { // 右左
    root->right = LL(root->right);
    return RR(root);
}
```
- [x] A1043
- [x] A1064
- [x] A1099
- [x] A1066
- [ ] A1107
- [ ] A1098
## 图算法
### pta中典型的dijkstra代码段
```cpp
int dist_to[maxn];
vector<int> edgeTo[maxn];
bool in_tree[maxn]{0};// false == 0
void dijkstra(int s, int d) {
    fill(dist_to, dist_to + maxn, INT_MAX);
    dist_to[s] = 0;
    while (min_vertex() != -1) {
        int v = min_vertex();
        for (int i = 0; i < n_city; i++) {
            if (G[v][i] < INT_MAX &&G[v][i] != 0) {
                if (dist_to[v] + G[v][i] < dist_to[i]) {
                    edgeTo[i].clear(); edgeTo[i].push_back(v);
                    dist_to[i] = dist_to[v] + G[v][i];
                }
                else if (dist_to[v] + G[v][i] == dist_to[i]) {
                    edgeTo[i].push_back(v); // important
                }
            }
        }
        in_tree[v] = true;
        if (v == d) break;
    }
}
int min_vertex(){
    int index = -1, min_dist = INT_MAX;
    for (int i = 0; i < n_city; i++) {
        if (!in_tree[i]) {
            if (dist_to[i] < min_dist) {
                min_dist = dist_to[i];
                index = i;
            }
        }
    }
    return index;
}
```
通常, 题目不会直接考dijkstra, 有四种形式的考法
- 求有多少条最短路径
- 给每条边一个额外权值, 求最短路径中权值和最优
- 给每个节点一个额外权值, 求最短路径中权值和最优
- 求更加复杂的二级优化条件
上述类型的题目, 总体思想都是先找到最短路径, 在所有最短路径中进行下一步比较或记数.
对于前三类问题, 可以直接在dijkstra过程中,通过增加一个数组的方式进行记录, 他们的特点是求和
对于第四类问题, (以及之前的问题) 可以通过对由edgeTo内容构成的图, 进行dfs的递归遍历, 找出所有最短路径,逐一比较并记录最优值
dfs的方法抓住两点: 递归边界——达到起点, 递归式——dfs其父节点.
用path_temp记录单条路径, 用path记录最优路径, 在当前节点离开dfs之前,从path_temp中pop出来, 保证了path_temp的干净, 也可以用类似的方法, 在离开当前节点前, 在复原temp值的现场.
代码模板:
```cpp
vector<int> path, temp_path;
int temp_value, opt_value;
void dfs(int v) {
    if (v == 起点) {
        temp_path.push_back(v);
        遍历temp_path, 计算temp_value;
        if (opt_value > temp_value) {
            opt_value = temp_value;
            path = temp_path;
        }    
    }
    else {
        temp_path.push_back(v);
        for (auto p : edgeTo[v])
            dfs(p);
    temp_path.pop_back();
    还原其他现场;
}
```
## 动态规划
动态规划的核心是重复子问题和最优子结构， 具有两个特点的问题才可能是动态规划问题。
- 和分治问题的区别: 分治问题和动态规划问题都有重复子问题, 分治问题的子问题不重复, 而动态规划的问题是有重复部分的.
- 和贪心问题的区别: 贪心问题和动态规划问题子结构, 但是贪心问题的解法是类似于"自顶向下"的一种思想, 不等到子结构中的最优解返回, 而是按照某种策略选择一个子结构不再考虑其他结构. 动态规划问题在处理时是"自底向上"的一种思想, 从边界开始求得最优子结构, 然后一步步往上求最优子结构. 在求最优子结构的时候会遇到重复解的情况, 需要保存以往的处理结果以供快速搜索.
最长不下降子序列LIS问题模板:
```cpp
int max_one = 0;
 for (int i = 0; i < num; i++) {
  dp[i] = 1;
  for (int j = 0; j < i; j++) {
   if (list[j] <= list[i]) {
    dp[i] = max(dp[j] + 1, dp[i]);
   }
  }
  if (max_one < dp[i]) max_one = dp[i];
 }
```
## 递归

递归的关键在于找到递归边界和递归关系式

## STL补充
### sort自定义比较函数
sort 的自定义cmp函数要用熟, 在写cmp函数的时候, 少用自己判断True 或false, 多用返回布尔表达式的方式
例如:
```cpp
if (p1.worth != p2.worth) return p1.worth > p2.worth;
else if (p1.age != p2.age) return p1.age < p2.age;
else return strcmp(p1.name, p2.name) < 0;
```
逻辑更加清晰
### upper_bound, lower_bound的使用方法
`upper_bound(first, last, value)` 左闭右开的区间, 返回第一个比value大的位置
`lower_bound(first, last, value)` 左闭右开的区间, 返回第一个大于等于value的元素的位置
### priority_queue的使用
priority里的优先级和vector里的优先级刚好相反, 自定义结构体的优先级时, 可以在struct里重载operator < 方法
```cpp
struct fruit {
    string name;
    int price;
    friend bool operator < (fruit f1, fruit f2) {
        return f1.price < f2.price;
    }
}
```
或者自定义一个struct对operator () 方法进行封装
```cpp
struct cmp {
    bool operator () (fruit f1, fruit f2) {
        return f1.price < f2.price;
    }
}
```
两种方式都可以设置priority_queue的优先级
### fill函数的使用
`fill(first, end, val)` 不像memset那这样限制-1或0, 允许是任意值