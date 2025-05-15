# Operator overload

- [Github with examples](https://github.com/vladuhalys/OperatorsOverloadingCPP/blob/master)
- [Obsure man page](https://en.cppreference.com/w/cpp/language/operators)

Operator overloading allows the programmer to define behavior for operators within a class. It allows classes to be compared, incremented, and manipulated as data types would.

```cpp
// without operator overload : 
// main.cpp:20:8: error: invalid operands to binary expression ('Fixed' and 'Fixed')
//        if (a == b)

int main( void ) {
 Fixed a(15.5f);
 Fixed b(15.51f);

 std::cout << a << " | " << b << std::endl;
 if (a == b)
  std::cout << "Yay !" << std::endl;
 else
  std::cout << "Aww :(" << std::endl;
 return 0;
}

// With operator overload : 
bool Fixed::operator==(const Fixed& comp) const {
 if  (this->raw == comp.getRawBits())
  return (true);
 return (false);
}

int main( void ) {
 Fixed a(15.5f);
 Fixed b(15.51f);

 std::cout << a << " | " << b << std::endl;
 if (a == b) // compiler can now evaluate equality
  std::cout << "Yay !" << std::endl;
 else
  std::cout << "Aww :(" << std::endl;
 return (0);
}
```

Most operators can be overloaded, with the exception of :

- scope resolution `::` ,
- member access `.` and `→` ,
- ternary conditional `?:`
- and `**`, `<` and `&|`

The syntax to overload common operators is as follows :

```cpp
    // Arithmetic Operators
    MyClass operator+(const MyClass& rhs) const;
    MyClass operator-(const MyClass& rhs) const;
    MyClass operator*(const MyClass& rhs) const;
    MyClass operator/(const MyClass& rhs) const;

    // Comparison Operators
    bool operator==(const MyClass& rhs) const;
    bool operator!=(const MyClass& rhs) const;
    bool operator<(const MyClass& rhs) const;
    bool operator>(const MyClass& rhs) const;
    bool operator<=(const MyClass& rhs) const;
    bool operator>=(const MyClass& rhs) const;

    // Assignment Operator
    MyClass& operator=(const MyClass& rhs);

    // Increment and Decrement Operators
    MyClass& operator++(); // Prefix increment
    MyClass& operator++(int); // Postfix increment
    // the parameter is here to differenciate the two operator++ function ; 
    // it is useless in the function and should be (void) 
    MyClass& operator--(); // Prefix decrement
    MyClass& operator--(int); // Postfix decrement
```

## Fixed Point Arithmetic

- [Arithmetic on fixed point numbers](https://spin.atomicobject.com/simple-fixed-point-math/)

## Templates & Overloaded functions

- [Overloaded functions](https://cplusplus.com/doc/tutorial/functions2/)

> templates are a secret tool that we will use later, so don't spend too much time thinking about that !

C++ allows functions to be **overloaded**, mean that several functions can share a name as long as they have a different number of parameters, or the parameters are of different types. This is what allows classes to possess multiple constructors.

**Important**
Overloaded functions, sharing the same name, should be used for similar purposes in order to maintain clarity and readability. For instance, having an overloaded `sum` function which in one case adds two parameters and in the second case substract them would be quite silly.

Overloaded functions often share the same body, and for that reason C++ allows the declaration of **templates**. A template is declared as such :

```cpp
template <typename SomeType>
SomeType sum (SomeType a, SomeType b)
{
  return a+b;
}
```

> `SomeType` can indiferrently be a class or a `typename`, which, in this case, are synonimous. [This guy](https://www.youtube.com/watch?v=86Pa973BW4Y) (video) argues that `typename` is more explicit to the user, because it signals that anything can be used in the templates, contrary to `class` that feels more limiting, even though the two are identical ; I quite agree and so recommend to use `typename`.

`SomeType`, once templated, becomes a placeholder for any data type you wish to use in your function. It be determined when the template is instantiated (used) in code.

> **Explicit vs implicit instanciation of a template** Templates can be instantiated implicitly or explicitely. Explicit instantiation is more optimized, providing a precompilation which saves time at compile time, while implicit instantiation occurs automatically. The compiler autogenerates code based on the value provided at time of use.

## Static Data Members

- [Static member variables](https://www.learncpp.com/cpp-tutorial/static-member-variables/)
- [Static member functions](https://www.learncpp.com/cpp-tutorial/static-member-functions/)
- [Static data member in CPP](https://www.learncpp.com/cpp-tutorial/static-member-functions/)

A static data member in CPP is declared using the `static` keyword. It can be a function or a variable, but all `static` members share those characteristics :

- Only one member will be created and shared by all objects of that class, no matter how many are created ;
- Static members are initialized before the main starts executing so that the static member can be used and accessed at any point ;
- Their lifetime encapsulate the entire duration of the program, meaning it starts with the program and the memory is destroyed when it ends ;
- They follow the same access rules as non-static data members (`private, protected or public`).

**When to use static data members:**

- Multiple objects need to share a ressource,
- We need global-like variable (static data is both safer and better structured),
- For expensive initialization data : it allows the variable to be initialized once, avoid the cost of repetition.
