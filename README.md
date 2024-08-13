### :memo: std::set_difference and std::back_inserter :1234:
```c++
set_difference -> Copies the elements from the sorted s1 which are not found in the sorted s2 to a container in sorted order
back_inserter -> Can be used to add elements to the end of a container
Example : 
        set<int> st1, st2;
	vector<int> v1;
	//Find difference in between set1 and set2 and put unique element of set1 in v1
	set_difference(begin(st1), end(st1), begin(st2), end(st2), back_inserter(v1));
	
	Qns on Leetcode: 2215
	Leetcode - : Find the Difference of Two Arrays

```
### :memo:Different ways of using priority_queue (i.e. heap) :mount_fuji:

- Default declarations
```c++
priority_queue<int> pq;                            //creates max-heap
priority_queue<int, vector<int>> pq;               //creates max-heap
```
<br>

- writing comparator function for priority_queue
```c++
1. Using in-built comparator provided by C++ : 

priority_queue<int, vector<int>, greater<int>> pq;  //creates min-heap
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>> > pq; //min_heap of pairs
priority_queue< pair<int, int>, vector<pair<int, int>>, greater<> > pq;               //min_heap of pairs
```
```c++
2. Using user defined comparator as a structure

struct comp {
    bool operator()(int &a, int &b) {
        return a<b; //max-heap
        return a>b; //min-heap
    }
};

priority_queue<int, vector<int>, comp> pq;  //usage
```

```c++
3. Using user defined comparator as a function

static bool comp(int &a, int &b) {
    return a<b; //max-heap
    return a>b; //min-heap
}

priority_queue<int, vector<int>, function<bool(int&, int&)> > pq(comp);   //usage
```
```c++
4. Using lambda function

auto comp = [](int &a, int &b) {
    return a<b; //max-heap
    return a>b; //min-heap 
};

priority_queue<int, vector<int>, decltype(comp) > pq(comp);   //usage

NOTE :
You can receive parameters inside [] as well i.e. auto comp = [some_parameters]
Ex : You want to access a map inside this lambda function
unordered_map<int, int> mp;

auto comp = [&mp](int &a, int &b) {
    return mp[a] < mp[b]; //etc.
};

```
