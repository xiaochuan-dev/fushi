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

