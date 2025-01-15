# The Coplien canonical class
- [The Coplien canonical class](https://eric.univ-lyon2.fr/ricco/cours/cours/au_coeur_de_la_prg_objet_cpp.pdf) (french)

The Coplien canonical form is standard to respect when creating classes. For a class to be canonical, the following methods must be defined : 

```cpp
class Class
	public:
		Class(void); // default constructor
		// or :
		Class(int i = 3); // default constructor
		Class(const Class&); // copy constuctor
		~Class(void); // destructor
		Class &operator=(const Class&); // assignement operator
```

## The default constructor
The default constructor takes no arguments (`Class(void)`) or for which each arguments has a default value. (`Class(int i = 3)`)
Default constructors allow the user to eliminate unexpected behaviors ; in the absence of a default constructor, compilers will attempt to provide one. Depending on the environement, the values within the class will be initialized to 0 or left empty ; I'm sure you can see how that could be an issue. 

```cpp
class Class
{
private:
	int i;
public:
	Class(int i = 3) { this->i = i; }
	void display(void) { std::cout << this->i << std::endl; }
};
```
Here, the constructor has a default value, which allows the compiler generated constructor to call it with that default value. If we were to do this : 

```cpp
class Class
{
private:
	int i;
public:
	Class(int i) { this->i = i; }
	void display(void) { std::cout << this->i << std::endl; }
};
```
We'd have the following error in main():

```cpp
int main(int, char**)
{
	Class tableau[3]; // no default constructor exists for class
	for (int i = 0; i < 3; i++)
		tableau[i].display();
}
```

## Copy constructor

- [What is a copy constructor ?](https://www.youtube.com/watch?v=UYYoq784pQY) (video)

**Copy constructor uses**
- Obviously duplicating an object, 
- When passing an instant by value to a method, the copy constructor is called to ensure that no modifications occur on the original instance, 
- If a function or method return a `Class` object, the copy constructor is called in order to allocate an instance on the heap for usage in the calling scope.

A copy constructor's purpose is to **create** an object from another one, taken as a model. If we do not provide one, the compiler *will* provide a default one. It is very important that one provides a copy constructor as soon as one is working with pointers. 
Without a provided copy constructor, the default constructor would attempt create copies of pointers, which means different instances of an object would use the same memory adresses.

This causes two main issues : 
- modification to the original instance would also appear on the copied one ;
- the destructors would try to delete the allocated blocks several times, as they have the same adresses, causing double frees.

Copy constructors are also needed to copy [aggregated classes](https://www.learncpp.com/cpp-tutorial/aggregation/) ; the aggregation model needs to be able to call the simpler objects copy constructors in order to be able to copy them.
> **Aggregation in short**
Aggregated classes are complex objects composed of several simpler ones. Aggregation models have a "has-a" relationship (a car *has-an* engine).

## Destructor
An explicit destructor is needed as soon as a class *allocates* memory. Its job is to deallocate the dynamic memory to render it available again.
If a class doesn't allocate memory dynamically, 

## Affectation operator
The `operator=()` is complementary to the copy constructor ; it is used to duplicate an instance in another when a copy constructor would be redundant. 
It's important to remember that while a copy constructor creates a new object from the ground up, the affectation operator may very well modify an existing object. As such, it may be pertinent to delete any allocated memory or aggregated objects in order to avoid issues. 