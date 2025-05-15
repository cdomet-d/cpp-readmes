# What is the point of reverse iterators ?

```cpp
int main()
{
 std::vector<char> fun;

 fun.push_back('0');
 fun.push_back('1');
 fun.push_back('2');
 fun.push_back('3');
 fun.push_back('4');
 fun.push_back('5');

 std::cout << "Forward" << std::endl;
 for (std::vector<char>::iterator it = fun.begin(); it != fun.end(); ++it) {
  if (*it == 0)
   std::cout << "N/A" << " ";
  std::cout << *it << " "; }
 
 std::cout << "\nBackward" << std::endl;
 for (std::vector<char>::iterator it = fun.end(); it != fun.begin(); --it) {
  if (*it == 0)
   std::cout << "N/A" << " ";
  std::cout << *it << " ";
 }

 std::cout << "\nReverse" << std::endl;
 for (std::vector<char>::reverse_iterator it = fun.rbegin(); it != fun.rend(); ++it) {
  if (*it == 0)
   std::cout << "N/A" << " ";
  std::cout << *it << " ";
 }

 std::cout << "\n.back()" << std::endl;
 std::cout << fun.back() << std::endl;
 std::cout << "\n.end()" << std::endl;
 std::cout << *fun.end() << std::endl;
}
```

```bash
Output :

Forward
0 1 2 3 4 5 
Backward
N/A  5 4 3 2 1 
Reverse
5 4 3 2 1 0 
.back()
5

.end()

```

## Conclusion

They are, indeed, useful.
