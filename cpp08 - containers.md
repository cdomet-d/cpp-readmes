# Content table

- [Content table](#content-table)
	- [Definition](#definition)
	- [Sequence containers](#sequence-containers)
	- [Associative containers](#associative-containers)
	- [Sources](#sources)

## [Definition](https://en.cppreference.com/w/cpp/named_req/Container)

A container contains things. It's very practical to have a way to store things, isn't it ? Even more so when you're working with memory, where looking for something where it isn't can result in bad stuff happening (see: segmentation fault).

In order to make our life easier, C++ offers several types of containers and their associated methods for handling. I encourage you to read the [sources](#sources) to gain a better understanding of those.

What I want to describe more here are the two different types of containers : **sequence** containers and **associative** containers.

## [Sequence containers](https://en.cppreference.com/w/cpp/named_req/SequenceContainer)

Sequence containers are simple containers that preserve the ordering of the elements you insert in them. You may also insert a new element at any given position. An _array_ is such a container; the STL (C++ Standard Template Library) offers a total of 6 sequence containers.

Four are in C++98

- [std::deque](https://en.cppreference.com/w/cpp/container/deque)
- [std::list](https://en.cppreference.com/w/cpp/container/list)
- [std::vector](https://en.cppreference.com/w/cpp/container/vector)
- and, technically, [std::basic_string](https://en.cppreference.com/w/cpp/string/basic_string)

Two new containers were added in C++11:

- [std::array](https://en.cppreference.com/w/cpp/container/array) ([more reading](https://thejat.in/learn/cpp-stdarray-in-cpp))
- [std::forward_list](https://en.cppreference.com/w/cpp/container/forward_list)

## [Associative containers](https://en.cppreference.com/w/cpp/named_req/AssociativeContainer)

Associative containers take your input and sort it ([or they don't](https://en.cppreference.com/w/cpp/named_req/UnorderedAssociativeContainer), from C++11). They do that based on _key_ values. Inserting a new element automatically sorts it in its place. They are known to garantee fast lookup of elements.

C++98:

- [std::set](https://en.cppreference.com/w/cpp/container/set) : for when you need a sorted, duplicate free array.
- [std::multiset](https://en.cppreference.com/w/cpp/container/multiset) : the same, but with duplicates
- [std::map](https://en.cppreference.com/w/cpp/container/map) : a sorted, duplicate free [key, value] container, structured as a red-black tree.
- [std::multimap](https://en.cppreference.com/w/cpp/container/multimap) : a map, but with duplicates

C++11:
> Introduces the unordered versions of the aforementionned containers. They are useful when, well, the sorting of your container doesn't matter.

- [std::unordered_set](https://en.cppreference.com/w/cpp/container/unordered_set)
- [std::unordered_multiset](https://en.cppreference.com/w/cpp/container/unordered_multiset)
- [std::unordered_map](https://en.cppreference.com/w/cpp/container/unordered_map)
- [std::unordered_multimap](https://en.cppreference.com/w/cpp/container/unordered_multimap)

C++23:
> Flat containers ensure continuous memory storage, which improves cache access. Those are the same associative containers than cited before, but flat.

- [std::flat_set](https://en.cppreference.com/w/cpp/container/flat_set)
- [std::flat_multiset](https://en.cppreference.com/w/cpp/container/flat_multiset)
- [std::flat_map](https://en.cppreference.com/w/cpp/container/flat_map)
- [std::flat_multimap](https://en.cppreference.com/w/cpp/container/flat_multimap)

## Sources

- [Container classes](https://www.learncpp.com/cpp-tutorial/container-classes/)
- [STL containers overview](https://www.learncpp.com/cpp-tutorial/stl-containers-overview/)
- [Complete course on containers and iterators](https://www.cs.cmu.edu/~gregjor/project/eckelbook/volume2/Chap07.htm)
- [Choose the right container](https://embeddedartistry.com/blog/2017/08/23/choosing-the-right-stl-container-general-rules-of-thumb/)
- [A general paper on the importance of choosing the right container, taking std::set as an example](https://lafstern.org/matt/col1.pdf)
- [What is the point of flat containers ?](https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0038r0.html)
