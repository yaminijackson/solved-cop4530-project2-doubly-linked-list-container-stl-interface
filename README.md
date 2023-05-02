Download Link: https://assignmentchef.com/product/solved-cop4530-project2-doubly-linked-list-container-stl-interface
<br>
Understanding generic programming and information hiding by developing generic containers. Getting familiar with the concept of class template and its usage. Use of nested (iterator) classes. Use of namespace. Operator overloading.

<strong>Task</strong>: Implement a doubly-linked list class template List and its associated iterators, with the same interface and iterator usage as that found in the C++ STL

<strong>Requirements</strong>:

<ol>

 <li>A header file List.h is provided, which contains the interfaces of the doubly-linked list class template List. In particular, it contains a nested Node structure, and two nested iterators class (iterator and const_iterator). You cannot change anything in the List.h file.</li>

</ol>

<ol>

 <li style="list-style-type: none;">

  <ul>

   <li><a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw2files/List.h">List.h</a></li>

  </ul></li>

</ol>

<ol start="2">

 <li>A driver program test_list.cpp has been included. It is an example test program that will run some tests on your implementation of the doubly-linked list class template for different data types (it tests List&lt;int&gt; and List&lt;string&gt;. Don’t make any changes to this driver program. However, your class will be tested with more than just this sample driver. It is recommended that you write other driver programs of your own, for more thorough testing.</li>

</ol>

<ol>

 <li style="list-style-type: none;">

  <ul>

   <li><a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw2files/test_list.cpp">test_list.cpp</a></li>

  </ul></li>

</ol>

<ol start="3">

 <li>You need to implement the member functions of the doubly-linked list class template List in a file named hpp. Note that List.hpp has been #included in the header file List.h (towards the end of the file). As we have discussed in class, you should not try to compile List.hpp (or List.h) by themselves. These comprise a header that will be #included into other programs you might write.</li>

</ol>

You need to implement all the member functions of List&lt;T&gt;, List&lt;T&gt;::iterator, and List&lt;T&gt;::const_iterator, and non-class overloaded functions operator==(), operator!=(), and operator&lt;&lt;() included in List.h. The design of the List container follows the one presented in the textbook. It has three member variables, theSize, head, and tail. theSize records the number of elements in the list. The head and tail pointers point to the sentinel nodes. They represent the beginning and end markers. They do not store any real elements in the list. It is OK for you to use the code provided in the textbook, but note that the definitions will be in the List.hpp file here, not defined inline in the class definition block, like they are in the textbook. Also, this implementation will contain more features than those in the textbook’s implementation, so there will be some new functions for you to write. We describe the requirements of each function in the following (this specification may not write the function prototypes in detail, so please refer to the List.h file for the detailed function prototype).

Member functions of nested const_iterator class:

<ul>

 <li>const_iterator(): default zero-parameter constructor. Set pointer <strong>current</strong> to nullptr.</li>

 <li>operator*(): returns a reference to the corresponding element in the list by calling retrieve() member function.</li>

 <li>operator++(), operator++(int), operator–(), operator–(int): prefix and postfix increment and decrement operators.</li>

 <li>operator==() and operator!=(): two iterators are equal if they refer to the same element.</li>

 <li>retrieve(): return a reference to the corresponding element in the list.</li>

 <li>const_iterator(Node *p): one-parameter constructor. Set pointer current to the given node pointer p.</li>

</ul>

Member functions of nested iterator class:

<ul>

 <li>iterator(): default zero-parameter constructor.</li>

 <li>operator*(): returns a reference to the corresponding element in the list by calling retrieve() member function.</li>

 <li>operator++(), operator++(int), operator–(), operator–(int): prefix and postfix increment and decrement operators.</li>

 <li>iterator(Node *p): one-parameter constructor.</li>

</ul>

Member functions of List class template

<ul>

 <li>List(): Default zero-parameter constructor. Call init() to initialize list member variables.</li>

 <li>List(const List &amp;rhs): Copy constructor. Create the new list using elements in existing list rhs.</li>

 <li>List(List &amp;&amp;rhs): move constructor.</li>

 <li>List(int num, const T &amp; val = T()): Construct a list with num elements, all initialized with value val.</li>

 <li>List(const_iterator start, const_iterator end): construct a List with elements from another list between start and end. Including the element referred to by the start iterator, but not the end iterator, that is [start, end).</li>

 <li>List(std::initializer_list&lt;T&gt; iList) : construct a List with elements from the initializer list that is passed in. Note that this will allow declarations like this:</li>

</ul>

List&lt;int&gt; myList {2, 4, 6, 8, 10, 12, 14, 16};

<ul>

 <li>~List(): destructor. You should properly reclaim all dynamically allocated memory</li>

 <li>operator=(List &amp;rhs): copy assignment operator</li>

 <li>operator=(List &amp;&amp;rhs): move assignment operator</li>

 <li>operator=(std::initializer_list&lt;T&gt; iList) : assign the initializer list data to be the calling object’s new data. Example call:</li>

</ul>

list2 = {1, 3, 5, 7, 9, 11, 13, 15};

<ul>

 <li>size(): return the number of elements in the List.</li>

 <li>empty(): return true if no element is in the list; otherwise, return false.</li>

 <li>clear(): delete all the elements in the list</li>

 <li>reverse(): reverse the order of the elements in the list. That is, the original first element becomes the last, while the original last becomes the first.</li>

 <li>front() and back(): return reference to the first and last element in the list, respectively.</li>

 <li>push_front() and push_back(), insert the new object as the first and last element into the list, respectively; and their move versions.</li>

 <li>pop_front() and pop_back(), delete the first and last element in the list, respectively.</li>

 <li>remove(const T &amp; val): delete all nodes with value equal to val from the list.</li>

 <li>remove_if(PREDICATE pred): delete all nodes for which pred returns true. PREDICATE is a template type, allowing a function object to be passed. (i.e. a true/false condition/function can be passed in via the functor).</li>

 <li>print(ostream &amp;os, char ofc = ‘ ‘): print all elements in the list, using character ofc as the deliminator between elements in the list.</li>

 <li>begin(): return iterator to the first element in the list.</li>

 <li>end(): return iterator to the end marker of the list (tail).</li>

 <li>insert(iterator itr, const T &amp; val): insert value val ahead of the node referred to by itr; and its move version</li>

 <li>erase(iterator itr): delete node referred to by itr. The return value is an iterator to the following node.</li>

 <li>erase(iterator start, iterator end): delete all nodes between start and end (including start but not end), that is, all elements in the range [start, end).</li>

 <li>init(): initialize the member variables of list.</li>

</ul>

Non-class functions

<ul>

 <li>operator==(const List&lt;T&gt; &amp; lhs, const List&lt;T&gt; &amp; rhs): check if two lists contain the same sequence of elements. Two lists are equal if they have the same number of elements and the elements at the corresponding position are equal.</li>

 <li>operator!=(const List&lt;T&gt; &amp; lhs, const List&lt;T&gt; &amp; rhs): opposite of operator==().</li>

 <li>operator&lt;&lt;(ostream &amp; os, const List&lt;T&gt; &amp; l): print out all elements in list l by calling List&lt;T&gt;::print() function.</li>

</ul>

<ol start="4">

 <li>Write a makefile for your project, to compile the test_list.cpp driver into an executable called proj2.x. Your program must be able to compile and run on the linprog machines.</li>

 <li>Analyze the worst-case run-time complexities of the member functions reverse() and remove_if(). Give the complexities in the form of Big-O. Your analysis can be informal; however, it must be clearly understandable by others. Name the file containing the complexity analysis as “analysis.txt”.</li>

</ol>

<strong>Downloads</strong>

Here again are links to the List.h and test drivers, as well as my output from the test_list.cpp driver program (myout.txt).

<ul>

 <li><a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw2files/List.h">List.h</a></li>

 <li><a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw2files/test_list.cpp">test_list.cpp</a></li>

 <li><a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw2files/myout.txt">myout.txt</a></li>

</ul>