# General concept : inheritance

- [Inheritance in CPP](https://www.youtube.com/watch?v=ptwZfAhI-kk&list=PLaatXkJEXKyKlx6H44MbV2d63AmudD5sd&index=1) (video playlist).

Class inheritance in CPP allows you to create a class that will get the attributes of a preexisting one.

Basically you can do that :

```cpp
class Ennemy {
 private:
 std::string name,
 int healthPoint,
 int actionPoints,
 int armorClass,

 public:
 void setName(std::string Name);
 void setHealth(int hp);
 void setActions(int ap);
 void setArmor(int ac);
 void displayName();
 int  getHealth();
 int  getActions();
 int  getArmor();
}
```

That's a very nice class ! Now imagine we need another class for a specific ennemy, let's say a dragon. It would be annoying to recreate a class from scratch, since we have a perfectly good Ennemy class ; but it isn't specific enough.

But a dragon **is an** ennemy, and so we can use the inheritance concept !

We'll do just that :

```cpp
class Ennemy {
 private:
 std::string name,
 int healthPoint,
 int actionPoints,
 int armorClass,

 public:
 void setName(std::string Name);
 void setHealth(int hp);
 void setActions(int ap);
 void setArmor(int ac);
 void displayName();
 int  getHealth();
 int  getActions();
 int  getArmor();
};

class Dragon : public Ennemy {
 private:
 std::string damageType;
 Weapon  weapon;
 
 public:
 int  breatheFire();
 int  wingClap();
 int  roar();
}
```

And here we have it ! `Dragon` inherited all the public attributes of `Ennemy`, allowing us to create a `Dragon` object that is also an `Ennemy`.
