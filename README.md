# 算法

## 基础

### 输入和输出

一直输入直到eof
```cpp
#include <cstdio>

int main() {
	int t;
	while (scanf("%d", &t) == 1) {
		// 其他输入 
		// 操作
		// 输出 
	}
	return 0;
}
 
```

输入直到输入为0

```cpp
#include <cstdio>

int main() {
	int t;
	while (scanf("%d", &t) == 1 && t) {
		// 其他输入 
		// 操作
		// 输出 
	}
	return 0;
}
 
```
一次输入两个数字
```cpp
#include <cstdio>

int main() {
	int t, p;
	while (scanf("%d%d", &t, &p) == 2 && t) {
		// 其他输入 
		// 操作
		// 输出
		printf("input is %d %d\n", t, p) ;
	}
	return 0;
}
 
```

输入n个例子
```cpp
#include <cstdio>

int main() {
	int t;
	scanf("%d", &t);
	while (t--) {
		// 输入
		// 处理
		// 输出 
	}
	return 0;
}
 
```

输出指定宽度和对齐方式
```cpp
#include <cstdio>

int main() {
	int a = 123;
	
	printf("%5d\n", a); // 这是右对齐，左边补0，输出 "  123"
    printf("%-5d\n", a); // 左对齐，右边补0 输出 "123  "

	return 0;
}

```

小数输出，保留3为小数
```cpp
#include <cstdio>
#include <cmath> 

int main() {
	double b = (double)10 / 3;
	
	printf("%.3f\n", b);
	return 0;
}
 
```

输入字符串，不能有空格

```cpp
#include <cstdio>
#include <cmath> 
#include <string>
#include <cstring> 

int main() {
	char i[100];
	scanf("%s", i); // 输入中不能有空格 
	
	std::string s = i;
	
	printf("input is %s\n", i);
	return 0;
}
 
```

输入字符串， 可以有空格
```cpp
#include <cstdio>
#include <cmath> 
#include <string>
#include <cstring> 

int main() {
	char i[100];
	gets(i); // gets函数直接输入
	
	std::string s = i;
	
	printf("input is %s\n", i);
	return 0;
}
 
```

### cpp基础


#### 字符串操作

```cpp
#include <cstdio>
#include <cmath> 
#include <string>
#include <cstring> 
#include <algorithm>

using namespace std;

int main() {
	string s = "hello world";
	
	string s1 = s + "hhhhhh";
	int l = s.length();
	char ch1 = s[0];
	
	bool b1 = s == "hello world";
	bool b2 = s != "hello world";
	bool b3 = s <= "hello worlf"; //字典序比较 
	
	int p1 = s.find("o"); 
	int p2 = s.find("world");
	int p3 = s.find("hhhh"); 		// 这是-1 
	
	bool b4 = s.empty(); 


	string s2 = s.substr(3, 4);		// 从index开始截取n个 
	
	printf("input is %s\n", s.c_str());
	return 0;
}
 
```

#### 字符串转换

```cpp
#include <cstdio>
#include <cctype>
#include <cstdlib> 
#include <string>

using namespace std;

int main() {
	// isalpha判断是不是字母 
	bool b1 = isalpha('a');
	bool b2 = isalpha('1');
	bool b3 = isdigit('4');		// 判断是不是数字字符 
	
	bool b4 = isalnum('4');		// 判断是不是数字或者字母 
	string str = "123";
    int n1 = std::stoi(str);	// 注意，std::stoi cpp11版本才能使用
	int n2 = atoi(str.c_str()); 	// atoi 把char* 转换成整数
	long n3 = atol(str.c_str());	// atol把char* 转换为long
	double b5 = atof("43.4314");	// atof把char*转换为double 
	
	return 0;
}
```

### cpp数据结构

#### vector

```cpp
#include <cstdio>
#include <vector>

using namespace std;

int main() {
	vector<int> v1;			// 初始化长度默认为0
	vector<int> v2(10);		// 初始化长度为10, 默认元素都是0
	vector<int> v3(10, 2);	// 初始化长度为10，元素为2 
	
	int n1 = v3.size();		// 获取当前的长度
	
	v3.push_back(10);      // 尾部添加
	v3.pop_back();         // 尾部删除

	int num1 = v3.front();	// 第一个元素 
	int num2 = v3.back();	// 最后一个元素 
	 	
	return 0;
}
```

#### set

```cpp
#include <cstdio>
#include <set>

using namespace std;

int main() {
	set<int> s1;		// 元素唯一自动排序
	s1.insert(3);
	s1.insert(1);
	
	s1.erase(1);
	
	bool e1 = s1.count(3); 		// 这个函数只能返回1或者0，可以直接用来判断在不在set里面
	bool e2 = s1.count(1); 
	
	s1.insert(0);
	
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		printf("%d\n", *it);
	}

	return 0;
}
```


#### map

map像set一样也会自动排序
```cpp
#include <cstdio>
#include <map>
#include <string>

using namespace std;

int main() {
	map<int, string> m;
	m.insert(make_pair(3, "world"));
	m.insert(make_pair(1, "hello")); 		// 通过pair插入 
	
	bool b1 = m.count(3);			// 判断是否存在 
	bool b2 = m.count(2);
	
	// 如果已经判断存在的话直接通过[]获取
	string s = m[3]; 
	
	m.erase(1);			// 按照key来删除 
	
	// 下面是类似于java中treemap的操作

	// 找到大于参数的第一个元素 ， 注意这里迭代器解引用之后是一个pair ， 还有一个函数是lower_bound
	map<int, string>::iterator it = m.upper_bound(2);
	if (it != m.end()) {
		pair<int ,string> s = *it;
		printf("found, key is %d value is %s\n", s.first, s.second.c_str());	
	}

	return 0;
}
```

#### stack

```cpp
#include <cstdio>
#include <stack> 

using namespace std;

int main() {
	stack<int> s;
	s.push(3);
	s.push(1);
	s.push(2);
	
	int n1 = s.top();
	s.pop();		// stl的stack pop函数不返回值 
	
	bool b = s.empty();
	
	return 0;
}
```

#### queue

```cpp
#include <cstdio>
#include <queue> 

using namespace std;

int main() {
	queue<int> q;
	// 入队 
	q.push(4);
	q.push(2);
	q.push(1);
	q.push(3);
	
	
	int num1 = q.front();
	int num2 = q.back();
	
	q.pop();		// 出队，同样不返回值 
	
	
	while (!q.empty()) {
		printf("%d\n", q.front());
		q.pop();
	}
	return 0;
}
```

#### deque

```cpp
#include <cstdio>
#include <deque> 

using namespace std;

int main() {
	deque<int> dq;
	dq.push_back(3);
	dq.push_front(1);
	int num1 = dq.front();
	int num2 = dq.back();
	dq.pop_back();
	dq.pop_back(); 

	return 0;
}
```

#### priority_queue

```cpp
#include <cstdio>
#include <vector> 
#include <queue> 
#include <functional>

using namespace std;

int main() {
	// 默认是最大堆 
	priority_queue<int> pq;
	pq.push(3);
	pq.push(5);
	int num1 = pq.top(); 
	
	pq.pop(); 	// 不返回值，stl的pop函数都不返回值
	
	// 最小堆，这里最后两个 > > 之间必须有空格 
	
	priority_queue<int, std::vector<int>, std::greater<int> > minHeap;
	minHeap.push(4);
	minHeap.push(2);
	minHeap.push(3);
	
	while (!minHeap.empty()) {
		printf("top is %d\n", minHeap.top());
		minHeap.pop();
	}
	
	return 0;
}
```

### algorithm

排序

```cpp
#include <cstdio>
#include <algorithm>
#include <vector>
#include <functional>

using namespace std;

int main() {
	
	int arr[] = {3, 1, 2, 4};
	int n = sizeof(arr) / sizeof(int);
	sort(arr, arr + n);		// 默认升序 
	
	int arr1[] = {3, 1, 2, 4};
	int n1 = sizeof(arr1) / sizeof(int);
	sort(arr1, arr1 + n1, greater<int>());		// 降序 
	
	vector<int> v;
	v.push_back(5);
	v.push_back(3);
	v.push_back(4);
	v.push_back(2);
	sort(v.begin(), v.end());  // 默认升序，也可以加fucntional里面的greater<int>()函数变成降序 
	int num1 = v[0];
	
	return 0;
}
```

第k大元素

```cpp
#include <cstdio>
#include <algorithm>
#include <vector>
#include <functional>

using namespace std;

int main() {
	
	int arr[] = {3, 1, 2, 4, 0};
	// 第二大的元素index在1,第一参数是开始的指针，第三参数是结尾指针 
	nth_element(arr, arr + 1, arr + 5);
	
	int res = arr[1];
	
	return 0;
}
```

查找下一个大于指定值的元素

`upper_bound`是找到第一个小于等于值的元素，默认也是使用在升序数组中，
```cpp
#include <cstdio>
#include <algorithm>
#include <vector>

using namespace std;

int main() {
	vector<int> v;
	v.push_back(4);
	v.push_back(2);
	v.push_back(1);
	
	sort(v.begin(), v.end());
	
	
	// 找到大于等于自己的元素，默认用在升序数组 
	vector<int>::iterator it = lower_bound(v.begin(), v.end(), 2);
	// 告诉编译器这是降序数组
    // vector<int>::iterator it2 = lower_bound(v.begin(), v.end(), 3, greater<int>());
	
	if (it != v.end()) {
		int pos = it - v.begin();
		printf("found %d position is %d\n", *it, pos);
	}
}
```

反转数组
```cpp
#include <cstdio>
#include <algorithm>
#include <vector>

using namespace std;

int main() {
	vector<int> v;
	v.push_back(4);
	v.push_back(2);
	v.push_back(1);
	
	reverse(v.begin(), v.end());
	return 0;
}
```

下一个排列
```cpp
#include <iostream>
#include <algorithm>
#include <vector>
using namespace std;

int main() {
    vector<int> v;
    v.push_back(2);
    v.push_back(1);
    v.push_back(3);
    
    do {
        for (int i = 0; i < v.size(); i++) {
            cout << v[i] << " ";
        }
        cout << endl;
    } while (next_permutation(v.begin(), v.end()));
    
    return 0;
}
```