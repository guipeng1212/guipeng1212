

# STL概述

![image-20210902211420181](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210902211420181.png)

![image-20210902211450242](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210902211450242.png)

![image-20210902211504165](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202015791.png)

![image-20210902211556516](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202016271.png)



# 初识stl



+ 三种遍历方法

~~~c++
#include <iostream>
using namespace std;
#include <vector>
#include <algorithm>//标准算法头文件

void myPrint(int val) {
	cout << val << endl;
}
//vector容器存放数据类型
void test01() {
	//创建数组
	vector <int> v;

	//插入数据
	v.push_back(10);
	v.push_back(20);
	v.push_back(30);
	v.push_back(40);
	v.push_back(50);

//	//通过迭代器访问1
//	vector<int>::iterator itBegin = v.begin();
//	vector<int>::iterator itEnd = v.end();
//
//	while (itBegin != itEnd) {
//		cout << *itBegin << endl;
//		itBegin++;
//	}

	////通过迭代器访问2
	//for (vector<int>::iterator it = v.begin(); it != v.end; it++) {
	//	cout << *it << endl;
	//}

	//通过迭代器访问3
	for_each(v.begin(), v.end(), myPrint);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~

+ 自定义数据类型

~~~c++
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
using namespace std;

class Person {
public:
	Person(string name, int age) {
		this->name = name;
		this->age = age;
	}
	string name;
	int age;
};

void test01() {
	Person p1("张三", 1);
	Person p2("张四", 2);
	Person p3("张五", 3);
	Person p4("张立", 4);
	vector<Person> person;


	person.push_back(p1);
	person.push_back(p2);
	person.push_back(p3);
	person.push_back(p4);

	for (vector<Person>::iterator it = person.begin(); it != person.end(); it++) {
		cout << "姓名：" << (*it).name << "年龄：" << (*it).age << endl;
	}
}
int main() {

	test01();
	system("pause");
	return 0;
}
~~~





# string容器



## 1.构造函数，使用了构造器

~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	const char *str = "helloworld";
	string s1(str);
	cout << s1 << endl;

	string str1 = str;
	cout << str1 << endl;

	string s2(s1);
	cout << s2 << endl;

	string s3(10, 'a');
	cout << s3 << endl;
}

int main() {

	test01();

	system("pause");
	return 0;
}
~~~



## 2.赋值操作，使用的是方法

<img src="https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202016621.png" alt="image-20210903145434619" style="zoom: 200%;" />





~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
    
    
    //等于号
	const char* s = "hello world";
	string str1;
	str1 = s;
	cout << "str1=	" << str1 << endl;

	
	string str2;
	str2 = 'c';
	cout << "str2=	" << str2 << endl;

	string str3;
	str3 = str1;
	cout << "str3=	" << str3 << endl;

    
    //方法
	string str4;
	str4.assign("hello C++");
	cout << "str4=	" << str4 << endl;


	string str5;
	str5.assign("hello C++", 5);
	cout << "str5=	" << str5 << endl;

	string str6;
	str6.assign(10, 'a');
	cout << "str6=	" << str6 << endl;
}



int main() {

	test01();

	system("pause");
	return 0;
}
~~~





## 3.字符串拼接

![image-20210903153056883](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210903153056883.png)



~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	string str1 = "我";
	str1 += "爱玩游戏";
	cout << "str1 =		" << str1 << endl;

	str1 += 'c';
	cout << "str1 =		" << str1 << endl;


	string str2 = "LOL";
	str1 += str2;
	cout << "str1 =		" << str1 << endl;


	string str3 = "I";
	str3.append(" love");
	cout << "str3 =		" << str3 << endl;

	str3.append("abcde", 4);
	cout << "str3 =		" << str3 << endl;

	string str4 = "I like";
	string str5 = str4;
	str4.append(str3);
	cout << "str4 =		" << str4 << endl;

	str5.append(str3, 0, 3);
	cout << "str5 =		" << str5 << endl;
}

int main() {

	test01();

	system("pause");
	return 0;
}
~~~





## 4.字符串的查找和替换

![image-20210903153219940](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210903153219940.png)



~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	int pos;
	string str1 = "abcdefde";
	(pos = str1.find("de")) == -1 ? cout << "没找到" << endl : cout << "找到了,pos=  " << pos << endl;

	(pos = str1.rfind("de")) == -1 ? cout << "没找到" << endl : cout << "找到了,pos=  " << pos << endl;
}

void test02() {
	string str1 = "abcdefde";
	cout << "str1" << str1 << endl;
	str1.replace(1, 3, "111");
	cout << "str1" << str1 << endl;
}

int main() {

	test01();
	test02();
	system("pause");
	return 0;
}
~~~





## 5.字符串的比较

![image-20210906171657708](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202016927.png)





## 6.单个字符的存取

![image-20210906171834490](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202016235.png)



~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	int i;
	string str1 = "abcdefde";
	cout << "str1   " << str1 << endl;
	string str2 = "abcedasd";
	if (str1.compare(str2)) {
		cout << "相等" << endl;
	}
	else {
		cout << "不相等" << endl;
	}
	str1[1] = '1';
	cout << "str1   " << str1 << endl;
	cout << "str[2]   " << str1[2] << endl;
	cout << "str[2]   " << str1.at(2) << endl;
}



int main() {

	test01();
	system("pause");
	return 0;
}
~~~



## 7.字符串的插入和删除

![image-20210906172544859](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202016302.png)





~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	int i;
	string str1 = "abcdefde";
	cout << "str1   " << str1 << endl;
	i = str1.size();
	string str2 = "abcedasd";
	
	str1.insert(str1.size(), str2);
	cout << "str1   " << str1 << endl;

	str1.erase(i,str2.size()+1);
	cout << "str1   " << str1 << endl;
}



int main() {

	test01();
	system("pause");
	return 0;
}
~~~



## 8.子串获取

![image-20210906173559626](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210906173559626.png)



~~~c++
#include <iostream>
using namespace std;
#include <string>

void test01() {
	int i;
	string str1 = "abcdefde";
	cout << "str1   " << str1 << endl;
	i = str1.size();
	string str2 = "1212312";

	string str3 = str1.substr(0, 3);
	cout << "str3  " << str3 << endl;

	str1.insert(i, str2);
	cout << "Substr  " << str1.substr(i,str2.size()) << endl;
}


void test02() {
	int i,find;
	string str1 = "abcdefde@qq.com";
	cout << "str1   " << str1 << endl;
	i = str1.size();
	string str2 = "1212312";

	find = str1.find('@');
	cout << "find  " << find << endl;
	cout << "Substr   " << str1.substr(0,find) << endl;
}


int main() {

	test01();
	test02();
	system("pause");
	return 0;
}
~~~





# vector容器

![image-20210907202258605](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210907202258605.png)





## 1.构造函数



![image-20210907203425624](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210907203425624.png)



~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it <<"  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;
	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);

	vector<int> v2(v1.begin(), v1.end());
	VectorTest(v2);
		
	vector<int> v3(10, 100);
	VectorTest(v3);

	vector<int> v4(v1);
	VectorTest(v4);
}

int main() {
	
	test01();
	system("pause");
	return 0;
}
~~~



## 2.函数赋值

![image-20210907205103776](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210907205103776.png)



~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;
	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);

	vector<int> v2;
	v2 = v1;
	VectorTest(v2);

	vector<int> v3;
	v3.assign(v1.begin(),v1.end());
	VectorTest(v3);

	vector<int> v4;
	v4.assign(10, 100);
	VectorTest(v4);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~



##3.容量和大小

![image-20210907205707322](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017649.png)



**empty方法：如果容器不为空，返回0，否则返回1，为空**

![image-20210907210648190](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017894.png)

~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;
	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);


	if (v1.empty()) {
		cout << "为空" << endl;
	}
	else {
		cout << "不为空" << v1.empty()<< endl;
	}

	cout << "容器的容量  " << v1.capacity() << endl;
	cout << "容器的元素个数   " << v1.size() << endl;
	
	v1.resize(v1.size() + 2, 4);
	VectorTest(v1);

	v1.resize(v1.size() - 2);
	VectorTest(v1);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~





## 4.容器中元素的插入和删除

**v.begin()和 v.end()就是迭代器iterator**

![image-20210907210842412](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017874.png)



![image-20210907211931591](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017497.png)

~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;
	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);

	v1.pop_back();
	VectorTest(v1);


	v1.insert(v1.begin(), 100);
	v1.insert(v1.end(), 100);
	v1.insert(v1.begin() + 2, 2, 55);
	VectorTest(v1);

	v1.erase(v1.begin());
	v1.erase(v1.begin(), v1.begin() + 2);
	VectorTest(v1);


	v1.clear();
	if (v1.empty()) {
		cout << "为空" << endl;
	}
	else {
		cout << "不为空" << v1.empty() << endl;
	}

}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~





## 5.数据存储

![image-20210911193806949](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017364.png)



![image-20210911194151314](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017898.png)

~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;
	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);

	for (i = 0; i < v1.size(); i++) {
		cout << v1.at(i) << "  ";
	}
	cout << endl;

	for (i = 0; i < v1.size(); i++) {
		cout << v1[i] << "  ";
	}
	cout << endl;

	cout << "front  " << v1.front() << endl;
	cout << "back  " << v1.back() << endl;
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~





## 6.容器交换



![image-20210911200705305](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017889.png)

~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	vector<int> v1;

	for (i = 0; i < 10; i++) {
		v1.push_back(i);
	}
	VectorTest(v1);
	
	vector<int> v2;
	for (i = 9; i >=0; i--) {
		v2.push_back(i);
	}
	VectorTest(v2);

	v1.swap(v2);
	VectorTest(v1);
}

void test02() {
	int i;
	

	vector<int> v2;
	for (i = 0; i <10000; i++) {
		v2.push_back(i);
	}
	cout << "容器的容量 " << v2.capacity() << endl;
	cout << "容器的大小  " << v2.size() << endl;
	v2.resize(3);

	cout << "容器的容量 " << v2.capacity() << endl;
	cout << "容器的大小  " << v2.size() << endl;
	vector<int>(v2).swap(v2);
	cout << endl;
	cout << "容器的容量 " << v2.capacity() << endl;
	cout << "容器的大小  " << v2.size() << endl;
}

int main() {

	test01();
	test02();
	system("pause");
	return 0;
}
~~~





## 7.预先设置容量

~~~c++
#include <iostream>
using namespace std;
#include <vector>

void VectorTest(vector<int> v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i,num=0;
	vector<int> v1;
	v1.reserve(1000);
	int *p = NULL;
	for (i = 0; i < 1000; i++) {
		v1.push_back(i);
		if (p != &v1[0]) {
			p = &v1[0];
			num++;
		}
	}
	cout << "次数  " << num << endl;
}

int main() {

	test01();

	system("pause");
	return 0;
}
~~~





# deque容器

![image-20210911203634021](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017163.png)

![image-20210911203648755](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017332.png)







## 1.构造函数

![image-20210911203705662](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017237.png)

![image-20210911204130212](C:\Users\gui\Desktop\数据结构笔记\image-20210911204130212.png)



~~~c++
#include <iostream>
using namespace std;
#include <deque>

void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	deque<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}

	DequePrint(v);

	deque<int> v1(v);
	DequePrint(v1);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~



## 2.赋值操作

![image-20210911204221402](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202017276.png)

![image-20210911204501036](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018937.png)



~~~c++
#include <iostream>
using namespace std;
#include <deque>

void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	deque<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}

	deque<int> v2;
	v2 = v;
	DequePrint(v2);

	deque<int> v3;
	v3.assign(v.begin(), v.end());
	DequePrint(v3);

	deque<int> v4;
	v4.assign(10, 23);
	DequePrint(v4);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~



## 3.大小操作

**注意：deque容器没有容量大小：他可以无限扩充**

![image-20210911204608814](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018788.png)

![image-20210911205008125](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018461.png)



~~~c++
#include <iostream>
using namespace std;
#include <deque>

void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	deque<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}
	DequePrint(v);
	if (v.empty()) {
		cout << "为空" << endl;
	}
	cout << "不为空" << endl << endl;
	cout << "大小  " << v.size() << endl;

	v.resize(13, 2);
	DequePrint(v);
	cout << "大小  " << v.size() << endl;
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~





## 4.插入和删除

![image-20210911205052477](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018316.png)

![image-20210911210621852](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018179.png)



~~~c++
#include <iostream>
using namespace std;
#include <deque>

void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	deque<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}
	DequePrint(v);
	
	v.push_front(1231);
	DequePrint(v);
	
	v.pop_back();
	DequePrint(v);

	v.pop_front();
	DequePrint(v);

	v.insert(v.begin()+1, 222);
	v.insert(v.begin() + 3, 3, 333);
	DequePrint(v);

	v.erase(v.begin());
	DequePrint(v);

	v.clear();
	if (v.empty()) {
		cout << "为空" << endl;
	}
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~



## 5.数据存取

![image-20210911210744499](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018419.png)



![image-20210911211058522](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018677.png)





~~~c++
#include <iostream>
using namespace std;
#include <deque>

void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


void test01() {
	int i;
	deque<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}
	
	for (i = 0; i < 10; i++) {
		cout << v[i] << "   ";
	}
	cout << endl;

	for (i = 0; i < 10; i++) {
		cout << v.at(i) << "   ";
	}
	cout << endl;

	cout << "头 " << v.front() << endl;
	cout << "尾  " << v.back() << endl;

}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~





## 6.排序



**#include <algoritm> 是标准算法头文件**

![image-20210911211147549](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018640.png)



![image-20210911211627946](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018171.png)



~~~c++
#include <iostream>
using namespace std;
#include <deque>
#include <algorithm>
void DequePrint(const deque<int> v) {
	for (deque<int>::const_iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

void test01() {
	
	deque<int> d;
	d.push_back(23);
	d.push_back(3);
	d.push_back(66);
	d.push_front(2);
	d.push_front(27);
	d.push_front(4);
	DequePrint(d);
    
	sort(d.begin(),d.end());
    
	DequePrint(d);
}

int main() {

	test01();
	system("pause");
	return 0;
}
~~~



# 打分案例



~~~c++
#include <iostream>
#include <vector>
#include <deque>
#include <string>
#include <algorithm>
using namespace std;

struct Participant {
	string name;
	double score;
};

void SetP(Participant *p) {
	int i = 0;
	double score;
	string name;
	cin >> name >> score;
	p->name = name;
	p->score = score;
}


void Print(vector <Participant> VectorP) {
	Participant p;
	for (vector<Participant>::iterator it = VectorP.begin(); it != VectorP.end(); it++) {
		p = *it;
		cout << "姓名：  " << p.name << "  成绩：  " << p.score << endl;
	}
}
void Printd(deque<double> d) {
	for (deque<double>::iterator it = d.begin(); it != d.end(); it++) {
		cout << *it << "  " << endl;
	}
}
double sumd(deque<double> d) {
	double sum=0;
	for (deque<double>::iterator it = d.begin(); it != d.end(); it++) {
		sum += *it;
	}
	return sum;
}
int main() {
	int i;
	Participant p1;
	Participant p2;
	Participant p3;
	Participant p4;
	Participant p5;
	vector <Participant> VectorP;
	SetP(&p1);
	SetP(&p2);
	SetP(&p3);
	SetP(&p4);
	SetP(&p5);
	VectorP.push_back(p1);
	VectorP.push_back(p2);
	VectorP.push_back(p3);
	VectorP.push_back(p4);
	VectorP.push_back(p5);
	
	Print(VectorP);

	deque<double> scoreD;
	for (vector<Participant>::iterator it = VectorP.begin(); it != VectorP.end(); it++) {
		scoreD.push_back(it->score);
	}
	sort(scoreD.begin(), scoreD.end());
	Printd(scoreD);
	scoreD.pop_back();
	scoreD.pop_front();
	cout << "目前去掉最高和最低分数：  " << endl;
	Printd(scoreD);
	cout << "目前总分：" <<sumd(scoreD) << endl;
	

	system("pause");
	return 0;
}
~~~







# Stack容器

![image-20210912205501352](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018639.png)



![image-20210913164446879](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018707.png)

~~~c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	stack<int> s;
	s.push(10);
	s.push(20);
	s.push(30);
	s.push(40);
	s.push(50);
	cout << "栈的大小：  " << s.size() << endl;
	while (!s.empty()) {
		cout << s.top() << endl;
		s.pop();
	}

	cout << "栈的大小：  " << s.size() << endl;


}

~~~



# queue容器

![image-20210913164418938](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018493.png)



![image-20210913171110972](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018392.png)





~~~c++
#include <iostream>
#include <queue>
#include <deque>
#include <string>
using namespace std;

struct Node {
	int score;
	string name;
}Node;

void Set(queue<struct Node> *Nodeq,int num) {
	int i = 0;
	for (i; i < num; i++) {
		struct Node pub;
		cout << "请输入姓名和分数" << endl;
		cin >> pub.name >> pub.score;
		(*Nodeq).push(pub);
	}
}
void Print(queue<struct Node> Nodeq) {
	while (!Nodeq.empty()) {
		cout << "姓名: " << Nodeq.front().name << "  分数: " << Nodeq.front().score << endl;
		Nodeq.pop();
	}
}
int main() {
	int i;
	queue<struct Node> Nodeq;
	cout << "请输入要添加的人数：  " << endl;
	cin >> i;
	Set(&Nodeq,i);
	Print(Nodeq);
	system("pause");
	return 0;
}
~~~





# List容器

![image-20210913171427436](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018239.png)





## 1.构造容器

![image-20210913171747069](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018908.png)



![image-20210913173013505](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018256.png)



~~~c++
#include <iostream>
#include <list>
using namespace std;


void Print(list<int> List) {
	for (list<int>::iterator it = List.begin(); it != List.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	int i;
	list<int> List;
	for (i = 0; i < 6; i++) {
		List.push_back(10 * i);
	}
	Print(List);

	list<int> List1 = List;
	Print(List1);
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~



## 2.赋值和交换

![image-20210913181904886](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018022.png)

![image-20210913182332332](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018539.png)

~~~c++
#include <iostream>
#include <list>
#include <algorithm>
using namespace std;


void Print(list<int> List) {
	for (list<int>::iterator it = List.begin(); it != List.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	int i;
	list<int> List;
	for (i = 0; i < 6; i++) {
		List.push_back(10 * i);
	}
	cout << "List:  " << endl;
	Print(List);
	list<int> List2;
	List2.assign(10, 34);
	cout << "List2:  " << endl;
	Print(List2);
	cout << "接下来是交换:  " << endl;
	swap(List, List2);
	cout << "List:  " << endl;
	Print(List);
	cout << "List2:  " << endl;
	Print(List2);
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~



## 3.大小操作

![image-20210913182448749](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018822.png)





## 4.插入和删除

![image-20210913182533380](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018524.png)

![image-20210913183241249](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202018139.png)



~~~c++
#include <iostream>
#include <list>
#include <algorithm>
using namespace std;


void Print(list<int> List) {
	for (list<int>::iterator it = List.begin(); it != List.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	int i;
	list<int> List;
	List.push_front(1);
	List.push_front(2);
	List.push_front(3);
	List.push_back(4);
	List.push_back(5);
	List.push_back(6);
	cout << "List:  " << endl;
	Print(List);

	List.pop_back();
	List.pop_front();
	cout << "List:  " << endl;
	Print(List);
	List.insert(++List.begin(), 34);
	cout << "List:  " << endl;
	Print(List);

	List.remove(34);
	cout << "List:  " << endl;
	Print(List);
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 5.数据存储

![image-20210913183513013](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019658.png)



![image-20210913183953323](C:\Users\gui\Desktop\数据结构笔记\c++学习.assets\image-20210913183953323.png)



![image-20210913183746954](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019796.png)

~~~c++
#include <iostream>
#include <list>
#include <algorithm>
using namespace std;


void Print(list<int> List) {
	for (list<int>::iterator it = List.begin(); it != List.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	int i;
	list<int> List;
	List.push_front(1);
	List.push_front(2);
	List.push_front(3);
	List.push_back(4);
	List.push_back(5);
	List.push_back(6);
	cout << "List:  " << endl;
	Print(List);

	List.pop_back();
	List.pop_front();
	cout << "List:  " << endl;
	Print(List);
	
	cout << "接下来显示单个数据： " << endl;
	cout << List.front() << endl;
	cout << List.back() << endl;
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 6.翻转和排序

![image-20210913184133713](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019581.png)

![image-20210913184358862](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019975.png)



~~~c++
#include <iostream>
#include <list>
#include <algorithm>
using namespace std;


void Print(list<int> List) {
	for (list<int>::iterator it = List.begin(); it != List.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	int i;
	list<int> List;
	List.push_front(1);
	List.push_front(2);
	List.push_front(3);
	List.push_back(4);
	List.push_back(5);
	List.push_back(6);
	cout << "List:  " << endl;
	Print(List);

	
	cout << "List:  " << endl;
	Print(List);
	
	cout << "接下来翻转： " << endl;
	List.reverse();
	Print(List);

	cout << "排序:  " << endl;
	List.sort();
	Print(List);
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 7.自定义条件排序

![image-20210913184726364](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019114.png)

![image-20210913184802637](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019964.png)







# Set容器

![image-20210914155204875](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019269.png)



## 1.构造和赋值

![image-20210914160007169](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019119.png)

~~~c++
#include <iostream>
#include <set>
using namespace std;


void PrintSet(set<int> s1) {
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	set<int> s1;

	s1.insert(12);
	s1.insert(52);
	s1.insert(62);
	s1.insert(17);
	s1.insert(13);
	//不允许输入重复值
	PrintSet(s1);

	set<int> s2 = s1;
	PrintSet(s2);
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~



## 2.大小和交换

![image-20210914160628948](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019540.png)

~~~c++
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
using namespace std;


void PrintSet(set<int> s1,string name) {
	cout << "打印" << name << ":  " << endl;
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	set<int> s1;

	s1.insert(12);
	s1.insert(52);
	s1.insert(62);
	s1.insert(17);
	s1.insert(13);
	PrintSet(s1,"s1");

	set<int>s2;
	s2.insert(10);
	s2.insert(50);
	s2.insert(70);
	s2.insert(40);

	PrintSet(s2, "s2");
	cout << "大小：  " << s1.size() << endl;
	cout << "交换操作：  "<<endl;

	swap(s1, s2);
	PrintSet(s1, "s1");
	PrintSet(s2, "s2");
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 3.插入和删除

![image-20210914160722291](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019228.png)

![image-20210914161309840](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019200.png)

~~~c++
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
using namespace std;


void PrintSet(set<int> s1, string name) {
	cout << "打印" << name << ":  " << endl;
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}
void test() {
	set<int> s1;

	s1.insert(12);
	s1.insert(52);
	s1.insert(62);
	s1.insert(17);
	s1.insert(13);
	PrintSet(s1, "s1");

	s1.erase(s1.begin());
	PrintSet(s1, "s1");

	s1.erase(62);
	PrintSet(s1, "s1");

	s1.clear();
	if (s1.empty()) {
		cout << "为空" << endl;
	}
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 4.查找和统计

![image-20210914161355506](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019771.png)

![image-20210914162653773](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019398.png)

~~~c++
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
using namespace std;


void PrintSet(set<int> s1, string name) {
	cout << "打印" << name << ":  " << endl;
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

int Find(set<int> s, int n) {
	set<int>::iterator it = s.find(n);
	return it != s.end() ? 1 : 0;
}
void test() {
	int s;
	set<int> s1;

	s1.insert(12);
	s1.insert(52);
	s1.insert(62);
	s1.insert(17);
	s1.insert(13);
	PrintSet(s1, "s1");

	cout << "请输入要查找的数"<<endl;
	cin >> s;
	Find(s1, s) == 1 ? cout << "找到了" << endl : cout << "没找到" << endl;

	cout << "统计12个数: " << s1.count(12) << endl;
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~





## 5.set和multiset的区别

![image-20210914163307190](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019722.png)

~~~c++
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
using namespace std;


void PrintSet(set<int> s1, string name) {
	cout << "打印" << name << ":  " << endl;
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

int Find(set<int> s, int n) {
	set<int>::iterator it = s.find(n);
	return it != s.end() ? 1 : 0;
}
void test() {
	int s;
	set<int> s1;
	s1.insert(12);
	s1.insert(52);
	s1.insert(62);
	s1.insert(17);
	s1.insert(13);
	PrintSet(s1, "s1");
	cout << "请输入要查找的数" << endl;
	cin >> s;
	Find(s1, s) == 1 ? cout << "找到了" << endl : cout << "没找到" << endl;
	cout << "统计12个数: " << s1.count(12) << endl;


	multiset<int> s2;
	s2.insert(10);
	s2.insert(10);
	s2.insert(10);
	s2.insert(10);
	s2.insert(10);
	for (multiset<int>::iterator it = s2.begin(); it != s2.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
	cout << "统计10的个数:  " << s2.count(10) << endl;
}

int main() {
	test();
	system("pause");
	return 0;
}
~~~



## 6.pair对组的创建

![image-20210914163414977](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019705.png)

![image-20210914164553792](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019958.png)

~~~c++
#include <iostream>
#include <set>
#include <algorithm>
#include <string>
using namespace std;


void test() {
	string name;
	int score;
	pair<string, int>p2 = make_pair("小明", 123);
	cout << "姓名：" << p2.first << "分数：  " << p2.second << endl;

}

int main() {
	test();
	system("pause");
	return 0;
}
~~~







# Map容器

![image-20210914165102713](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019579.png)





## 1.构造和赋值

![image-20210914165351365](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019535.png)



![image-20210914170235589](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019109.png)

~~~c++
#include <iostream>
#include <map>
#include <string>
using namespace std;

void Print(map<int, string>m1) {
	for (map<int, string>::iterator it = m1.begin(); it != m1.end(); it++) {
		pair<int, string>m = *it;
		cout << "编号：  " << m.first << " " << "姓名：" << m.second << endl;
	}
}

void test() {
	map<int, string>m1;
	m1.insert(pair<int,string>(1,"张三"));
	m1.insert(pair<int, string>(2, "李四"));
	m1.insert(pair<int, string>(3, "王二麻子"));
	Print(m1);
}
int main() {

	test();
	system("pause");
	return 0;
}
~~~



## 2.大小和交换

![image-20210914171233841](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019839.png)



~~~c++
#include <iostream>
#include <map>
#include <string>
#include <algorithm>
using namespace std;

void Print(map<int, string>m1) {
	for (map<int, string>::iterator it = m1.begin(); it != m1.end(); it++) {
		pair<int, string>m = *it;
		cout << "编号：  " << m.first << " " << "姓名：" << m.second << endl;
	}
}

void test() {
	map<int, string>m1;
	m1.insert(pair<int, string>(1, "张三"));
	m1.insert(pair<int, string>(2, "李四"));
	m1.insert(pair<int, string>(3, "王二麻子"));
	cout << "m1:  " << endl;
	Print(m1);

	map<int, string>m2;
	m2.insert(pair<int, string>(1, "张si"));
	m2.insert(pair<int, string>(2, "李we"));
	m2.insert(pair<int, string>(3, "王二der"));
	cout << "m2:  " << endl;
	Print(m2);

	m1.empty() ? cout<<"为空" <<endl :cout<< "不为空" << endl;

	swap(m1, m2);
	cout << "m1:  " << endl;
	Print(m1);
	cout << "m2:  " << endl;
	Print(m2);
}
int main() {

	test();
	system("pause");
	return 0;
}
~~~





## 3.插入和删除

![image-20210914171347786](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202019976.png)

![image-20210914172309864](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020856.png)



~~~c++
#include <iostream>
#include <map>
#include <string>
#include <algorithm>
using namespace std;

void Print(map<int, string>m1) {
	for (map<int, string>::iterator it = m1.begin(); it != m1.end(); it++) {
		pair<int, string>m = *it;
		cout << "编号：  " << m.first << " " << "姓名：" << m.second << endl;
	}
}

void test() {
	map<int, string>m1;
	m1.insert(pair<int, string>(1, "张三"));
	m1.insert(make_pair(2, "李四"));
	m1.insert(map<int, string>::value_type(3, "王二麻子"));
	cout << "m1:  " << endl;
	Print(m1);

	m1.erase(1);
	cout << "m1:  " << endl;
	Print(m1);

	m1.erase(m1.begin());
	cout << "m1:  " << endl;
	Print(m1);
}
int main() {

	test();
	system("pause");
	return 0;
}
~~~





## 4.查找和统计

![image-20210914173559143](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020631.png)



~~~c++
#include <iostream>
#include <map>
#include <string>
#include <algorithm>
using namespace std;

void Print(multimap<int, string>m1) {
	for (multimap<int, string>::iterator it = m1.begin(); it != m1.end(); it++) {
		pair<int, string>m = *it;
		cout << "编号：  " << m.first << " " << "姓名：" << m.second << endl;
	}
}

int Find(multimap<int, string>m1, int n) {
	return m1.find(n) != m1.end() ? 1 : 0;
}
void test() {
	int n,i;
	multimap<int, string>m1;
	m1.insert(pair<int, string>(1, "张三"));
	m1.insert(make_pair(2, "李der"));
	m1.insert(make_pair(2, "李四"));
	m1.insert(make_pair(2, "李sie"));
	m1.insert(map<int, string>::value_type(3, "王二麻子"));
	cout << "m1:  " << endl;
	Print(m1);

	cout << "请输入你要找到的编号: " << endl;
	cin >> n;
	Find(m1, n) == 1 ? cout << "找到了" << endl : cout << "没找到" << endl;

	cout << "请输入你要找到的编号: " << endl;
	cin >> n;
	multimap<int, string>::iterator it = m1.find(n);
	if (it != m1.end()) {
		for (i = 0; i < m1.count(n); i++) {
			cout << "编号： " << it->first << "姓名： " << it->second << endl;
			it++;
		}
		
	}


	cout << "统计个数:  " << endl;
	cin >> n;
	cout << n << "编号的个数:  " << m1.count(n)  <<  endl;


}
int main() {

	test();
	system("pause");
	return 0;
}
~~~







## 5.排序

![image-20210914174250710](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020980.png)

![image-20210914174223501](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020541.png)

~~~c++
#include <iostream>
#include <map>
#include <string>
#include <algorithm>
using namespace std;

class My {
public:
	bool operator()(int v1, int v2) {
		return v1 > v2;
	}
};

void Print(multimap<int, string, My>m1) {
	for (multimap<int, string, My>::iterator it = m1.begin(); it != m1.end(); it++) {
		pair<int, string>m = *it;
		cout << "编号：  " << m.first << " " << "姓名：" << m.second << endl;
	}
}

void test() {
	int n, i;
	multimap<int, string, My>m1;
	m1.insert(pair<int, string>(1, "张三"));
	m1.insert(make_pair(2, "李der"));
	m1.insert(make_pair(2, "李四"));
	m1.insert(make_pair(2, "李sie"));
	m1.insert(map<int, string>::value_type(3, "王二麻子"));
	cout << "m1:  " << endl;
	Print(m1);


}
int main() {

	test();
	system("pause");
	return 0;
}
~~~



# 员工分组

![image-20210914193926762](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020027.png)



~~~c++
#include <iostream>
using namespace std;
#include <map>
#include <vector>
#include <string>
#include <ctime>
class Worker {
public:
	int money;
	string name;

	
};

void creatWorker(vector<Worker> *wor) {
	int i;
	string T = "ABCDEFGHIJ";
	for (i = 0; i < 10; i++) {
		Worker w;
		w.name = "员工";
		w.name += T[i];
		w.money = rand() % 10000 + 10000;
		wor->push_back(w);
	}
}

void SetMap(multimap<int, Worker> *WorMap, vector<Worker> wor) {
	for (vector<Worker>::iterator it = wor.begin(); it != wor.end(); it++) {
		int department = rand() % 3 + 1;
		WorMap->insert(make_pair(department, *it));
	}
}

void Find(multimap<int, Worker> WorMap,int n) {
	int count,i;
	multimap<int, Worker>::iterator it = WorMap.find(n);
	if (it != WorMap.end()) {
		count = WorMap.count(n);
		for (i = 0; i < count; i++) {
			cout << "部门编号：" << it->first << "  姓名： " << it->second.name << "  工资：  " << it->second.money << endl;
			it++;
		}
	}
}

int main() {
	int n;

	srand((unsigned int)time(NULL));
	vector<Worker> wor;
	creatWorker(&wor);
	
	multimap<int, Worker> WorMap;
	SetMap(&WorMap, wor);

	cout << "请输入你要找到部门编号：" << endl;
	cin >> n;
	Find(WorMap, n);
	system("pause");
	return 0;
}
~~~





# 函数对象

![image-20210914194111983](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022773.png)



## 1.基本使用

![image-20210914194738891](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020645.png)

![image-20210914194800165](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020306.png)

![image-20210914194839897](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020412.png)





## 2.一元谓词

![image-20210914195339172](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020659.png)



## 3.二元谓词

![image-20210914195436617](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020362.png)







# 内建函数对象

![image-20210914195602514](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020096.png)



## 1.算数仿函数

![image-20210914195626036](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020365.png)



![image-20210914195839149](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020204.png)





## 2.关系仿函数

![image-20210914195950363](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202020366.png)



![image-20210914200055304](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021506.png)





## 3.逻辑仿函数

![image-20210914200143028](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021179.png)



![image-20210914200351985](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021590.png)







# 常用遍历算法



## 1.for_each



![image-20210915171600698](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021372.png)



![image-20210915172111507](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021572.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>


class print01 {
public:
	void operator() (int val) {
		cout << val << "  ";
	}
};
int main() {
	int i;
	vector<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i * 10);
	}

	for_each(v.begin(), v.end(),print01());

}
~~~



## 2.transform

**需要提前开辟要存的对象空间**

![image-20210915172200675](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021900.png)

![image-20210915172828719](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/image-20210915172828719.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>


class print01 {
public:
	void operator() (int val) {
		cout << val << "  ";
	}
};

class trans {
public:
	int operator() (int val) {
		return val;
	}
};
int main() {
	int i;
	vector<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i * 10);
	}

	for_each(v.begin(), v.end(), print01());

	vector<int> v2;
	v2.resize(v.size());
	transform(v.begin(), v.end(), v2.begin(), trans());
	cout << endl;
	for_each(v2.begin(), v2.end(), print01());
}
~~~





![image-20210915172932511](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021250.png)

![image-20210915172939647](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021908.png)





# 常见查找算法

![image-20210915173147547](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021579.png)

## 1.find

~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>



int main() {
	int i;
	vector<int> v;
	for (i = 0; i < 10; i++) {
		v.push_back(i);
	}

	find(v.begin(), v.end(), 50) == v.end() ? cout << "没找到：" << endl : cout << "找到了： " << endl;


	
}
~~~



**如果要是自定义的类型，就需要自己设置查找方式**



![image-20210915174152914](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021353.png)





## 2.find_if



![image-20210915180008226](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021031.png)



**自定义的数据类型**

![image-20210915174613465](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021637.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>
#include <string>
class Person {
public:
	int age;
	string name;

	Person(int age, string name) {
		this->age = age;
		this->name = name;
	}

	bool operator ==(const Person per){
		if (this->name == per.name && this->age == per.age) {
			return true;
		}
		else {
			return false;
		}
	}
};

class Per {
public:
	bool operator()(Person per) {
		return per.age > 20;
	}
};

int main() {
	int i;
	vector<Person> per;
	Person p1(23, "张三");
	Person p2(26, "张sg");
	Person p3(24, "张df");
	Person p4(2, "张d");

	per.push_back(p1);
	per.push_back(p2);
	per.push_back(p3);
	per.push_back(p4);
	
	vector<Person>::iterator it = find_if(per.begin(), per.end(), Per());
	if (it != per.end()) {
		int count = count_if(per.begin(), per.end(), Per());
		for (i = 0; i < count; i++) {
			cout << "年龄： " << it->age << "  姓名：  " << it->name << endl;
			it++;
		}
	}

}
~~~



## 3.adjacent_find

![image-20210916163042014](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021944.png)

![image-20210916163442186](C:\Users\gui\Desktop\数据结构笔记\c++学习.assets\image-20210916163442186.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>



int main() {
	int i;
	vector<int> v;
	v.push_back(0);
	v.push_back(1);
	v.push_back(1);
	v.push_back(0);
	v.push_back(3);
	v.push_back(4);
	v.push_back(4);

	vector<int>::iterator it = adjacent_find(v.begin(), v.end());
	if (it != v.end()) {
		cout << "找到了" << *it << endl;
	}



}
~~~



## 4.binary_search (二分查找法)

**必须是有序序列**

![image-20210916163514019](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202021153.png)

![image-20210916163803942](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022230.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>



int main() {
	int i;
	vector<int> v;
	v.push_back(0);
	v.push_back(1);
	v.push_back(4);
	v.push_back(6);
	v.push_back(3);
	v.push_back(56);
	v.push_back(7);
	sort(v.begin(), v.end());
	bool sus = binary_search(v.begin(), v.end(),56);
	if (sus) {
		cout << "找到了" << endl;
	}



}
~~~



## 5.count

![image-20210916163927425](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022564.png)

![image-20210916164149613](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022554.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>

int main() {
	int i;
	vector<int> v;
	v.push_back(0);
	v.push_back(1);
	v.push_back(4);
	v.push_back(6);
	v.push_back(6);
	v.push_back(6);
	v.push_back(6);
	v.push_back(6);
	v.push_back(3);
	v.push_back(56);
	v.push_back(7);
	int sus = count(v.begin(), v.end(),6);
	cout << "个数:" << sus << endl;

}
~~~



## 6.count_if

![image-20210916164819747](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022057.png)

![image-20210916165358847](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022453.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>
#include <string>
class Person {
public:
	int age;
	string name;

	Person(int age, string name) {
		this->age = age;
		this->name = name;
	}

	bool operator ==(const Person per) {
		if (this->name == per.name && this->age == per.age) {
			return true;
		}
		else {
			return false;
		}
	}
};

class Per {
public:
	bool operator()(Person per) {
		return per.age == 2;
	}
};

int main() {
	int i;
	vector<Person> per;
	Person p1(23, "张三");
	Person p2(26, "张sg");
	Person p3(24, "张df");
	Person p4(2, "张d");
	Person p5(2, "网d");
	Person p6(2, "佛d");
	Person p7(2, "张d");

	per.push_back(p1);
	per.push_back(p2);
	per.push_back(p3);
	per.push_back(p4);
	per.push_back(p5);
	per.push_back(p6);
	per.push_back(p7);

	int sus = count_if(per.begin(), per.end(), Per());
	cout << "age为2的人数：  " << sus << endl;

}
~~~







# 常见排序算法

![image-20210916165437213](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022207.png)

![image-20210916173309563](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022151.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>


void Print(vector<int> &v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

int main() {
	int i;
	vector<int> v;
	vector<int> v2;
	vector<int> v3;
	for (i = 0; i < 10; i++) {
		v2.push_back(i);
	}
	v.push_back(0);
	v.push_back(1);
	v.push_back(4);
	v.push_back(6);
	v.push_back(62);
	v.push_back(5);
	v.push_back(78);
	v.push_back(9);
	v.push_back(10);
	v.push_back(56);
	v.push_back(7);
    
    cout << "排序" << endl;
	sort(v.begin(), v.end());
	Print(v);

	cout << "随机排序" << endl;
	random_shuffle(v.begin(), v.end());
	Print(v);

	cout << "容器翻转" << endl;
	reverse(v.begin(), v.end());
	Print(v);

	cout << "容器合并" << endl;
	v3.resize(v.size() + v2.size());
	sort(v.begin(), v.end());
	sort(v2.begin(), v2.end());
	merge(v.begin(), v.end(), v2.begin(), v2.end(), v3.begin());
	Print(v3);

	
}
~~~





# 拷贝和替换

![image-20210916173519326](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022041.png)

![image-20210916174710733](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022651.png)



~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>

class Mypac {
public:
	bool operator()(int val) {
		return val > 11;
	}
};

void Print(vector<int> &v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}


int main() {
	int i;
	vector<int> v;
	vector<int> v2;
	vector<int> v3;
	for (i = 0; i < 10; i++) {
		v2.push_back(i);
	}
	v.push_back(0);
	v.push_back(1);
	v.push_back(4);
	v.push_back(6);
	v.push_back(62);
	v.push_back(5);
	v.push_back(78);
	v.push_back(9);
	v.push_back(10);
	v.push_back(56);
	v.push_back(7);

	cout << "排序并且打印v: " << endl;
	sort(v.begin(), v.end());
	Print(v);

	cout << "copy并且打印v2: " << endl;
	v2.resize(v.size());
	copy(v.begin(), v.end(), v2.begin());
	Print(v2);

	cout << "replace并且打印v: " << endl;
	for (i = 0; i < v.size(); i++) {
		replace(v.begin(), v.end(), v[i], i);
	}
	Print(v);

	cout << "swap并且打印v: " << endl;
	swap(v, v2);
	cout << "打印v: " << endl;
	Print(v);
	cout << "打印v2: " << endl;
	Print(v2);

	cout << "replace_if并且打印v: " << endl;
	replace_if(v.begin(), v.end(), Mypac(),300);
	Print(v);

	
}
~~~





# 常见的算数生成算法

**要包含numeric**

![image-20210916175007779](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022758.png)

![image-20210916174753124](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022408.png)

![image-20210916175539011](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022184.png)

~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>
#include <numeric>

void Print(vector<int> &v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

int main() {
	int i;
	vector<int> v;
	vector<int> v2;
	vector<int> v3;
	for (i = 0; i < 10; i++) {
		v2.push_back(i);
	}
	v.push_back(0);
	v.push_back(1);
	v.push_back(4);
	v.push_back(6);
	v.push_back(62);
	v.push_back(5);
	v.push_back(78);
	v.push_back(9);
	v.push_back(10);
	v.push_back(56);
	v.push_back(7);

	cout << "计算容器的元素总和" << endl;
	int total = accumulate(v.begin(), v.end(),0);
	cout << "总和：  " << total << endl;

	cout << "fill算法" << endl;
	fill(v.begin(), v.end(), 0);
	Print(v);
}
~~~





# 常用的集合算法



**注意：必须要提前对两个容器进行相同的排序操作**



![image-20210916175614465](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022389.png)



![image-20210916192502275](https://raw.githubusercontent.com/guipeng1212/Photo/main/img/202109202022896.png)

~~~c++
#include <iostream>
#include <algorithm>
using namespace std;
#include <vector>

void Print(vector<int> &v) {
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++) {
		cout << *it << "  ";
	}
	cout << endl;
}

class Myprint {
public:
	void operator()(int val) {
		cout << val << "  ";
	}
};

int main() {
	int i;
	vector<int> v;
	vector<int> v2;
	vector<int> v3;
	for (i = 0; i < 10; i++) {
		v2.push_back(i);
		v.push_back(i + 3);
	}

	cout << "容器v ：" << endl;
	Print(v);
	cout << "容器v2 ：" << endl;
	Print(v2);
	cout << "两个容器的交集 ：" << endl;
	v3.resize(min(v.size(),v2.size()));
	vector<int>::iterator it = set_intersection(v.begin(),v.end(),v2.begin(),v2.end(),v3.begin());
	for_each(v3.begin(),it, Myprint());
	
	cout << endl<< "两个容器的并集 ：" << endl;
	v3.resize(v.size()+v2.size());
	vector<int>::iterator it1 = set_union(v.begin(), v.end(), v2.begin(), v2.end(), v3.begin());
	for_each(v3.begin(), it1, Myprint());


	cout << endl << "两个容器的差集 ：" << endl;
	v3.resize(v.size() + v2.size());
	vector<int>::iterator it2 = set_difference(v.begin(), v.end(), v2.begin(), v2.end(), v3.begin());
	for_each(v3.begin(), it2, Myprint());
}
~~~

