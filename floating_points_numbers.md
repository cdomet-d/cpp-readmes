# General ressources & definitions

- General concept : [Floating point numbers](https://youtu.be/PZRI1IfStY0?si=y4NEsHVebhyHYUgJ) (video)

# The concepts of floats

A float is a representation of a decimal number. While `intergers` holds an exact value, while a `floating point` number is the representation of a decimal number. That representation, plus the fact that the floating point value is *interpreted*, can cause issues in precision.

## Accuracy vs Precision

In programming, `accuracy` and `precision` are distinct concepts that must be differentiated.

- **Accuracy** refers to how close you are from the true value of an element ;
- **Precision** is how much information you have about an element.

`integers` are by essence extremely accurate, but they lack precision ; `2 == 2` and `(2 + 1) == 3` . As long as we don’t overflow, integer manipulation will always end up matching the expected result bit by bit. They are, however. unable to maintain decimal value, such that both `4 / 2` and `5 / 2` are equal to `2` . We have lost **precision**. 

`floating point numbers` are not as accurate, but they are much more precise. Think of it as `1/3` . It's technically equal to 0.3, with an infinity of 3 after the `.`, so we represent it as 0.333333, but it is imprecise ; some numbers cannot be precisely represented, and so in some cases, the result of a floating point operation will never meet the true result. 

A good analogy is presented [here](https://www.cprogramming.com/tutorial/floating_point/understanding_floating_point.html), in the following quote :

> Integers are too "chunky" to represent these finer gradations; using them is like building with bricks. If you want to make a cube, you know the bricks can represent it perfectly, but a sphere wouldn't come out quite as well. Floating point numbers are the exact opposite of integers with respect to accuracy and precision. They have good precision, since they never deliberately discard information representing your numbers. (...) But floating point numbers have poor accuracy. If ints are like bricks, then floats might be thought of as silly putty. You have enough control to mold them into complex curved shapes, but they leave something to be desired when it comes to forming a specified target shape. Imagine trying to make a perfect cube out of silly putty—you'll never get those corners as sharp as they should be.
## Floating point representation

Floating point representation varies from machine to machine, but a standard is used these days in order to simplify the matter : the IEEE-754 standard. That standard allows for portability and compatibility, and is composed  of three “blocks” as follows : 

- **a sign block** which tells if the number stored is positive or negative,
- **an exponent** that defines the size of the number,
- **a mantissa**, which contains the digits of the number stored.

# What is a fixed point number and why do we care ?

According to StackOverflow user [Gabe](https://stackoverflow.com/users/310574/gabe) in [this post](https://stackoverflow.com/questions/7524838/fixed-point-vs-floating-point-number): 

> A fixed point number has a specific number of bits (or digits) reserved for the integer part (the part to the left of the > decimal point) and a specific number of bits reserved for the fractional part (the part to the right of the decimal point). No matter how large or small your number is, it will always use the same number of bits for each portion. For example, if your fixed point format was in decimal IIIII.FFFFF then the largest number you could represent would be 99999.99999 and the smallest non-zero number would be 00000.00001. Every bit of code that processes such numbers has to have built-in knowledge of where the decimal point is.

> A floating point number does not reserve a specific number of bits for the integer part or the fractional part. Instead it reserves a certain number of bits for the number (called the mantissa or significand) and a certain number of bits to say where within that number the decimal place sits (called the exponent). So a floating point number that took up 10 digits with 2 digits reserved for the exponent might represent a largest value of 9.9999999e+50 and a smallest non-zero value of 0.0000001e-49.

Fixed points numbers are used when one needs to use decimal numbers, but also need performance over precision.