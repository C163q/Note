- [算法笔记](#算法笔记)
	- [基础知识](#基础知识)
		- [对数器](#对数器)
		- [比较器](#比较器)
		- [快慢指针](#快慢指针)
		- [master公式](#master公式)
		- [树](#树)
			- [先序遍历（深度优先遍历）](#先序遍历深度优先遍历)
			- [中序遍历](#中序遍历)
			- [后序遍历](#后序遍历)
			- [宽度优先遍历（层次遍历）](#宽度优先遍历层次遍历)
			- [搜素二叉树](#搜素二叉树)
			- [完全二叉树](#完全二叉树)
			- [平衡二叉树 以及二叉树解题套路](#平衡二叉树-以及二叉树解题套路)
			- [最低公共祖先](#最低公共祖先)
			- [树形dp](#树形dp)
			- [Morris遍历](#morris遍历)
			- [大数据（1）](#大数据1)
			- [大数据（2）](#大数据2)
		- [图](#图)
			- [宽度优先遍历](#宽度优先遍历)
			- [深度优先遍历](#深度优先遍历)
			- [拓扑排序算法](#拓扑排序算法)
			- [kruskal算法（最小生成树）](#kruskal算法最小生成树)
			- [prim算法（最小生成树）](#prim算法最小生成树)
			- [Dijkstra算法（某点到其他点的最短距离）](#dijkstra算法某点到其他点的最短距离)
			- [哈希表与哈希函数](#哈希表与哈希函数)
			- [布隆过滤器](#布隆过滤器)
			- [一致性哈希](#一致性哈希)
			- [并查集 O(1) 《算法导论》23章](#并查集-o1-算法导论23章)
			- [Manacher算法](#manacher算法)
	- [算法](#算法)
		- [冒泡排序 O(n^2)](#冒泡排序-on2)
		- [选择排序 O(n^2) *无排序稳定性*](#选择排序-on2-无排序稳定性)
		- [插入排序 O(n^2)](#插入排序-on2)
		- [归并排序 O(n\*logN) *额外空间复杂度O(N)*](#归并排序-onlogn-额外空间复杂度on)
		- [类快速排序问题 O(N) *额外空间复杂度O(1)*](#类快速排序问题-on-额外空间复杂度o1)
		- [快速排序 *(无排序稳定性)*](#快速排序-无排序稳定性)
		- [堆（heap）与heap insert *(时间复杂度：O(logN))*](#堆heap与heap-insert-时间复杂度ologn)
		- [heapify *(时间复杂度：O(N))*](#heapify-时间复杂度on)
		- [堆排序 *(时间复杂度：O(NlogN)，空间复杂度：O(1)，无排序不稳定)*](#堆排序-时间复杂度onlogn空间复杂度o1无排序不稳定)
		- [计数排序(桶) *(时间复杂度：O(N)，普适性差)*](#计数排序桶-时间复杂度on普适性差)
		- [基数排序(桶) *(时间复杂度：O(N)，普适性差)*](#基数排序桶-时间复杂度on普适性差)
		- [排序稳定性](#排序稳定性)
		- [排序总结](#排序总结)
		- [前缀树](#前缀树)
		- [贪心算法](#贪心算法)
			- [时间安排](#时间安排)
			- [字符串拼接](#字符串拼接)
			- [切割金条（哈夫曼编码问题）](#切割金条哈夫曼编码问题)
			- [做项目](#做项目)
		- [暴力递归（动态规划基础）](#暴力递归动态规划基础)
			- [汉诺塔问题](#汉诺塔问题)
		- [暴力递归 -\> 动态规划](#暴力递归---动态规划)
			- [机器人运动](#机器人运动)
			- [零钱兑换](#零钱兑换)
	- [题目](#题目)
		- [出现奇数次的数（1个）](#出现奇数次的数1个)
		- [出现奇数次的数（2个）](#出现奇数次的数2个)
		- [获取数据流中的中位数](#获取数据流中的中位数)
		- [N皇后问题 以及常数时间的优化](#n皇后问题-以及常数时间的优化)
		- [RandomPool结构（哈希表的应用）](#randompool结构哈希表的应用)
		- [岛问题](#岛问题)
		- [KMP算法](#kmp算法)
		- [滑动窗口问题](#滑动窗口问题)
		- [单调栈（最近较大值问题）](#单调栈最近较大值问题)
		- [位运算题目](#位运算题目)


# 算法笔记

## 基础知识

### 对数器
**概念：** 为了测试算法的正确性，可以使用两种算法，并且用随机样本生成器生成样本，如果大量样本在两个算法中跑出的结果相同，大概率两个样本的结果是正确的，否则是错误的。

### 比较器
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：1:37:31

### 快慢指针
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=6)
时间：1:23:23

用例：单链表要知道自己走到的位置位于一半时，用快指针一次走两步，慢指针一次走一步，当快指针到终点，慢指针就到达一半位置。

### master公式
**概念：** 用于剖析递归行为和递归行为的时间复杂度。

公式为`T(N) = a*T(N/b) + O(N^d)`，其中T(N)中N为母问题的数据量，N/b为子问题的数据量，a为母问题转化为的子问题数，O(N^d)为递归外其他行为时间复杂度。有以下结果：

`log(b,a) > d` -> 复杂度为`O(N^log(b,a))`

`log(b,a) = d` -> 复杂度为`O(N^d * logN)`

`log(b,a) < d` -> 复杂度为`O(N^d)`

相关网址：
[算法的复杂度与 Master 定理](https://blog.gocalf.com/algorithm-complexity-and-master-theorem)

### 树
#### 先序遍历（深度优先遍历）
递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:02:13

非递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:09:56
#### 中序遍历
递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:05:38

非递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:21:47
#### 后序遍历
递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:06:51

非递归法：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:16:40
#### 宽度优先遍历（层次遍历）
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=7)
时间：1:45:58

计算单层结点最多的结点数

#### 搜素二叉树
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=8)
时间：02:25

判断方法

#### 完全二叉树
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=8)
时间：20:08

#### 平衡二叉树 以及二叉树解题套路
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=8)
时间：37:56

#### 最低公共祖先
解法一：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=8)
时间：1:22:52

解法二：
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=8)
时间：1:33:22

#### 树形dp
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=15)
时间：02:06

#### Morris遍历
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=15)
时间：39:28

#### 大数据（1）
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=15)
时间：1:45:32

#### 大数据（2）
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=16)
时间：03:08


### 图
#### 宽度优先遍历
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：39:56

#### 深度优先遍历
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：49:53

#### 拓扑排序算法
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：1:00:04

#### kruskal算法（最小生成树）
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：1:12:27

#### prim算法（最小生成树）
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：1:41:33

#### Dijkstra算法（某点到其他点的最短距离）
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=9)
时间：1:59:18

#### 哈希表与哈希函数
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=12)
时间：02:59

#### 布隆过滤器
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=12)
时间：1:07:57

n = 样本量 , P = 失误率 , m = bitset位个数 , k = 哈希函数数量

`m = -(n * lnP) / (ln2)^2`

`k = ln2 * m / n`

`P = (1 - e^(-n * k / m))`

#### 一致性哈希
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=12)
时间：1:58:51

#### 并查集 O(1) 《算法导论》23章
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=13)
时间：25:08

#### Manacher算法
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=14)
时间：02:47




## 算法

### 冒泡排序 O(n^2)
**原理：** 将数组中的最大的数放到数组的最后，将次之的数放在倒数第二的位置，直至将所有元素排完。

**实现方法：** 第一层循环遍历最后一个元素到第二个元素，保证当前元素比之前的所有元素都大。第二层循环遍历第一个到第一层选定元素前的一个元素，遍历时，当自身大于后一个元素时，两者交换，最终最大的元素便浮上来。依次遍历，排序完成。

**代码：**

````C
void swap(int* a, int* b) {         // 交换元素的函数
	int tmp = *a;
	*a = *b;
	*b = tmp;
}
void BubbleSort(int arr[], int n) {     // 冒泡排序算法
	for (int i = n - 1; i > 0; i--) {
		for (int j = 0; j < i; j++) {
			if (arr[j] > arr[j + 1])
				swap(&arr[j], &arr[j + 1]);
		}
	}
}
````
````C++
template<typename It,typename func>
inline void bubble_sort(const It begin,const It end, func f) {
	for (auto it = std::prev(end); it != begin; --it) {
		for (auto p = begin; p != it; ++p) {
			if (f(p[1], *p)) {
				std::swap(p[1], *p);
			}
		}
	}
}

template<typename It>
inline void bubble_sort(const It begin, const It end) {
	bubble_sort(begin, end, std::less<>());
}
````



### 选择排序 O(n^2) *无排序稳定性*
**原理：** 选出数组中最小的元素，放在最前面，选出次小的，放在第二个，依次进行直至排序完成。

**实现方法：** 第一层循环遍历第一个到倒数第二个元素，保证当前元素比后面的都小。第二层循环遍历当前元素到最后一个元素，选出最小的元素与自身交换。依次遍历，排序完成。

**代码：**

````C
void swap(int* a, int* b) {         // 交换元素的函数
	int tmp = *a;
	*a = *b;
	*b = tmp;
}
void SelectionSort(int arr[], int n) {     // 选择排序算法
	for (int i = 0; i < n - 1; i++) {
		int pos = i, min = arr[i];
		for (int j = i; j < n; j++) {
			if (arr[j] < min) {
				pos = j;
				min = arr[j];
			}
		}
		swap(&arr[i], &arr[pos]);
	}
}
````
````C++
template<typename It, typename func>
inline void selection_sort(const It begin, const It end, func f) {
	for (auto it = begin; it != std::prev(end); ++it) {
		auto p = it;
		auto min = *p;
		for (auto iter = std::next(it); iter != end; ++iter) {
			if (f(*iter, min)) {
				p = iter;
				min = *iter;
			}
		}
		if (p != it) std::swap(*it, *p);
	}
}

template<typename It>
inline void selection_sort(const It begin, const It end) {
	selection_sort(begin, end, std::less<>());
}
````


### 插入排序 O(n^2)
**原理：** 从头遍历数组元素，保证对于某个元素，其与之前的所有元素都是有序的。

**实现方法：** 第一层循环遍历第二个元素到最后一个元素。第二层循环遍历该元素前一个元素到第一个元素，如果该元素大于后一个元素，交换，并向前移动；如果小于等于，停止并返回第一层循环。依次遍历，排序完成。

**代码：**

````C
void swap(int* a, int* b) {         // 交换元素的函数
	int tmp = *a;
	*a = *b;
	*b = tmp;
}
void InsertionSort(int arr[], int n) {      // 插入排序的算法
	for (int i = 1; i < n; i++) {
		for (int j = i - 1; j >= 0 && arr[j] > arr[j + 1]; j--) {
            // 此处可能会提前终止循环，因此可能会好于O(n^2)
			swap(&arr[j], &arr[j + 1]);
		}
	}
}
````
````C++
template<typename It, typename func>
inline void insertion_sort(const It begin, const It end, func f) {
	for (auto it = std::next(begin); it != end; ++it) {
		for (auto iter = it; iter != begin; --iter) {
			if (f(*iter, *std::prev(iter))) {
				std::swap(*iter, *std::prev(iter));
			}
			else break;
		}
	}
}

template<typename It>
inline void insertion_sort(const It begin, const It end) {
	insertion_sort(begin, end, std::less<>());
}
````


### 归并排序 O(n*logN) *额外空间复杂度O(N)*
**原理：** 一个数组，利用递归分一半，让左侧有序，让右侧有序，最后让整个数组有序。

**实现方法：** 先递归不断左右对半分，当左右两侧分别只有一个数字时，停止并合并，合并时，使用双指针使数组有序，先创建一个数组，左边部分和右边部分初始时均指向第一个元素，当左小于右时，左为新数组第一个元素，左指针右移；否则为右。

**代码：**

````C++
void merge(int arr[], int l, int mid, int r) {
	int* p = new int[r - l + 1];
	int i = 0, p1 = l, p2 = mid + 1;
	while (p1 <= mid && p2 <= r) {		// 取较小值存入临时数组中
		if (arr[p1] <= arr[p2]) {
			p[i++] = arr[p1++];
		}
		else {
			p[i++] = arr[p2++];
		}
	}
	while (p1 <= mid) {		// 未放入临时数组的元素依次放入
		p[i++] = arr[p1++];
	}
	while (p2 <= r) {
		p[i++] = arr[p2++];
	}
	for (i = 0; i <= r - l; i++) {	// 排好的序列放回原数组
		arr[l + i] = p[i];
	}
	delete[] p;
}
void MergeSort(int arr[], int l, int r) {
	if (l == r) return;
	int mid = l + (r - l) / 2;		// 取中点，防溢出
	// 可以写成 int mid = l + ((l - r) >> 1) 来加快运算速度
	MergeSort(arr, l, mid);			// 折半递归
	MergeSort(arr, mid + 1, r);
	merge(arr, l, mid, r);		// 使左右两侧数组有序
}
````
````C++
template<typename It,typename func>
inline void _merge(const It begin, const It end, const It mid, func f) {	// end为最后一个元素
	using val = typename std::iterator_traits<It>::value_type;
	val* tmp = new val[std::distance(begin, end)+1];
	auto it1 = begin;
	auto it2 = std::next(mid);
	size_t i = 0;
	while (it1 != std::next(mid) && it2 != std::next(end)) {
		if (!f(*it2, *it1)) {
			tmp[i++] = *it1++;
		}
		else {
			tmp[i++] = *it2++;
		}
	}
	while (it1 != std::next(mid)) {
		tmp[i++] = *it1++;
	}
	while (it2 != std::next(end)) {
		tmp[i++] = *it2++;
	}
	for (i = 0, it1 = begin; i <= size_t(std::distance(begin, end)); ++i, ++it1) {
		*it1 = tmp[i];
	}
	delete[] tmp;
}

template<typename It, typename func>
void _merge_sort(const It begin, const It end, func f) {		// end为最后一个元素
	if (begin == end) return;
	auto mid = begin + (std::distance(begin, end) >> 1);
	_merge_sort(begin, mid, f);
	_merge_sort(std::next(mid), end, f);
	_merge(begin, end, mid, f);
}

template<typename It,typename func>
inline void merge_sort(const It begin, const It end, func f) {
	_merge_sort(begin, std::prev(end), f);
}

template<typename It>
inline void merge_sort(const It begin, const It end) {
	merge_sort(begin, end, std::less<>());
}
````

### 类快速排序问题 O(N) *额外空间复杂度O(1)*
用于将小于等于num的放左侧，大于num的放右侧。

将小于num的放左侧，大于num的放右侧，等于的放中间。

[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=4)
时间：1:44:07

### 快速排序 *(无排序稳定性)*
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=4)
时间：2:02:20；3.0版本：2:16:48（O(N*logN)）*额外空间复杂度O(logN)*
````C++
template<typename It,typename func>
inline std::pair<It, It> _sort_partition(const It begin, const It end, func f) {	// end为最后一个元素
	std::pair<It, It> res(std::prev(begin), end);
	auto p = begin;
	while (p != res.second) {
		if (f(*p, *end)) {
			++res.first;
			std::swap(*res.first, *p++);
		}
		else if (f(*end, *p)) {
			--res.second;
			std::swap(*res.second, *p);
		}
		else
			++p;
	}
	std::swap(*end, *res.second++);
	return res;
}

template<typename It, typename func, typename engine>
void _quick_sort(const It begin, const It end, func f, engine& dre) {	// end为最后一个元素
	if (!(begin < end)) return;
	ptrdiff_t dis = std::distance(begin, end);
	std::uniform_int_distribution<ptrdiff_t> distri(0, dis);
	std::swap(*end, *(begin + distri(dre)));
	std::pair<It, It> res = _sort_partition(begin, end, f);
	_quick_sort(begin, res.first, f, dre);
	_quick_sort(res.second, end, f, dre);
}


template<typename It,typename func,typename engine>
inline void quick_sort(const It begin, const It end, func f,engine& dre) {
	_quick_sort(begin, std::prev(end), f, dre);
}

template<typename It, typename func>
inline void quick_sort(const It begin, const It end, func f) {
	std::default_random_engine dre(time(nullptr) % std::numeric_limits<uint32_t>::max());
	quick_sort(begin, end, f, dre);
}

template<typename It>
inline void quick_sort(const It begin, const It end) {
	quick_sort(begin, end, std::less<>());
}
````


### 堆（heap）与heap insert *(时间复杂度：O(logN))*
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：07:38

### heapify *(时间复杂度：O(N))*
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：29:26

### 堆排序 *(时间复杂度：O(NlogN)，空间复杂度：O(1)，无排序不稳定)*
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：50:53

优化(总体复杂度级别不变)：上述视频时间: 1:08:51
````C++
template<typename It,typename func>
inline void _heap_insert(const It begin, It pos, func f) {				// end为最后一个元素
	auto father = begin + (std::distance(begin, pos) - 1) / 2;
	while (f(*father, *pos)) {
		std::swap(*pos, *father);
		pos = father;
		father = begin + (std::distance(begin, pos) - 1) / 2;
	}
}

template<typename It, typename func>
inline void _heapify(const It begin, const It end, It pos, func f) {	// end为最后一个元素
	auto left = begin + ((std::distance(begin, pos) << 1) + 1);
	while (left <= end) {
		auto largest = (left != end && f(*left, *(left + 1)) ? left + 1 : left);
		largest = f(*pos, *largest) ? largest : pos;
		if (largest == pos) break;
		std::swap(*largest, *pos);
		pos = largest;
		left = begin + ((std::distance(begin, pos) << 1) + 1);
	}
}

template<typename It,typename func>
inline void _heap_sort(const It begin, const It end, func f) {			// end为最后一个元素
	if (std::distance(begin, end) < 1) return;
	auto p = begin;
	for (++p; p != std::next(end); ++p) {	// O(N)
		_heap_insert(begin, p, f);			// O(logN)
	}
	p = end;
	std::swap(*begin, *p);
	while (p != begin) {					// O(N)
		_heapify(begin, --p, begin, f);		// O(logN)
		std::swap(*begin, *p);				// O(1)
	}
}

template<typename It,typename func>
inline void heap_sort(const It begin, const It end, func f) {
	_heap_sort(begin, std::prev(end), f);
}

template<typename It>
inline void heap_sort(const It begin, const It end) {
	heap_sort(begin, end, std::less<>());
}
````



### 计数排序(桶) *(时间复杂度：O(N)，普适性差)*
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：1:51:21

### 基数排序(桶) *(时间复杂度：O(N)，普适性差)*
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=5)
时间：1:58:22

### 排序稳定性
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=6)
时间：02:44

### 排序总结
目前没有发现时间复杂度低于O(N*logN)的通用排序算法

目前没有发现时间复杂度为O(N*logN)且稳定的,空间复杂度小于O(N)的通用排序算法

快速排序经过实验表明是最快的排序，应当尽量使用。

### 前缀树
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)
时间：05:05

### 贪心算法
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)
时间：58:13

#### 时间安排
已知多个会议的开始和结束时间，使安排时间不重叠的情况下最多的安排数（贪心：考虑会议结束最早的）

[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)

#### 字符串拼接
多个字符串，求出使字符串拼接起来字典序最小的拼接方法（贪心：若a拼接b小于b拼接a，则a放前，b放后）

[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)

#### 切割金条（哈夫曼编码问题）
一根金条，切割为二所消耗的铜板数等于其长度，求出切割为指定多个长度的金条所消耗的最少的铜板数

[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)

#### 做项目
初始资金已知，最多能做的项目已知，每个项目的耗费和利润已知，求在最佳决策的情况下最多得到多少

[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)

### 暴力递归（动态规划基础）
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=11)
时间：41:51

#### 汉诺塔问题
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=11)
时间：44:36

### 暴力递归 -> 动态规划
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=17)
时间：03:02

暴力递归 -> 记忆化搜素(dp) -> 严格表结构(dp) -> 严格表优化

#### 机器人运动
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=17)
时间：09:06

#### 零钱兑换
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=17)
时间：1:00:10




## 题目

### 出现奇数次的数（1个）

**题目：** 一个数组中，只有一个数出现了奇数次，其余数出现了偶数次，求该数字。

- ***1.***
**使用异或 O(n) ：**

**原理：** 一个数异或本身为0,0异或一个数等于那一个数。

**实现方法：** 将数组中的所有元素异或一遍，得到结果。

**代码：**
````C
int solution(int arr[], int n) {    // 解法
	int a = 0;
	for (int i = 0; i < n; i++) {
		a ^= arr[i];
	}
	return a;   // 该值为结果
}
````


### 出现奇数次的数（2个）
**题目：** 一个数组中，只有两个数出现了奇数次，其余数出现了偶数次，求这两个数字。

- ***1.***
**使用异或 O(n) ：**

**原理：** 使用[出现奇数次的数（1个）](#出现奇数次的数1个)的方法最后得到的结果为这两个数字的异或，由于这两个数字不同，所以这两个数字一定有一位不同（即异或为1），只要将原数列中这一位为1的全部异或一遍，就可以得到两数当中的一个，从而可以得到另外一个。

**实现方法：** 使用[出现奇数次的数（1个）](#出现奇数次的数1个)的方法最后得到的结果为这两个数字（设为a、b）的异或，得到异或结果中最右侧以为不为0的位，将原数组中所有该位为1的数异或一遍，得到a或b，将该数异或a^b，得到另一个数。

**代码：**
````C
#include<stdio.h>
void solution(int arr[], int n) {	// 解法，设结果为a、b
	int eor = 0;
	for (int i = 0; i < n; i++) {
		eor ^= arr[i];		// eor = a ^ b
	}
	int right = eor & (~eor + 1);	// 提取出最右侧的1，right为二进制中最右侧一的表示
	int a = 0;
	for (int i = 0; i < n; i++) {
		if (arr[i] & right)
			a ^= arr[i];
	}
	int b = eor ^ a;
	printf("%d %d\n", a, b);	// a和b为解
}
````

### 获取数据流中的中位数
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)
时间：2:17:04

### N皇后问题 以及常数时间的优化
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=10)
时间：2:28:01

### RandomPool结构（哈希表的应用）
[视频链接](https://www.bilibili.com/video/BV13g41157hK/?p=12)
时间：54:24

### 岛问题
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=13)
时间：04:27

### KMP算法
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=13)
时间：1:28:02

### 滑动窗口问题
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=14)
时间：1:42:52

### 单调栈（最近较大值问题）
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=14)
时间：2:11:14（无重复值），2:31:17（有重复值）

### 位运算题目
[视频链接](https://www.bilibili.com/video/BV13g41157hK?p=16)
时间：1:06:56


