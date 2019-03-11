# udemy_csharp-intermediate

1a) Classes

What is a Class made of (what are its Members)?
* Data (represented by fields)
* Behaviour (represented by methods)

What is an Object? An Instance of a class

Member Accessibility:
* Instance members are accessible from an Object
* Static members are accessible from a Class

Styling:
* PascalCase for Class and Method names
* camelCase for Fields, and _camelCase for private Fields

1b) Constructors - Putting an Object in an early state

If no Constructor is given, one is created that sets fields to their default values:
* Numbers - 0
* Booleans - false
* Reference - null
* Character - empty

1c) Object Initializers - Creating an Object by giving it Data properties in the constructor

1d) Methods

What is a Method Signature? The Name, and Number and Type of parameters
What is Overloading? A Method with the same Name, but differing parameters
What is the 'params' modifier? Allows a variable number of arguments to be given
What is the 'ref' modifier? (Code Smell) Allows your method to modify a given parameter, rather than working on a local copy
What is the 'out' modifier? (Code Smell) Allows you to return multiple values from the method to the caller

1e) Fields

What is the 'readonly' modifier? Such a variable can only be defined on construction/ initialization

1f) Access Modifiers

Critical for 'Encapsulation'. In practice, this is defining fields as private and providing public getter/ setter methods.

1g) Properties

What is a Property? A class member that encapsulates a getter/ setter for a field.
e.g. `private DateTime _birthdate` and `public DateTime Birthdate { get{return _birthdat;} set{_birthdate = value;} }`

1h) Indexers

What is an Indexer? A way to access elements in a class that represent a list of values.
Without them, we'd have to write a get method for the collection.
e.g. var item = array`[0]`;

2a) Coupling

What is Coupling? A measure of how interconnected classes and subsystems are.
Tightly coupled classes are a negative, as small changes may affect other parts of the application.

2b) Relationships - Inheritance

What is Inheritance? An 'Is-a' relationship between two classes that allows one to be a version of another.
Example: Car might be a Parent Class, and a specific model might be a Child Class
`public class Car {}` and `public class AlfaRomeoSpyder : Car {}`

2c) Relationships - Composition

What is Composition? A 'Has-a' relationship between two classes that allows one to contain the other.
Example: Car might be a Parent Class, and Engine might be a Child Class
`public class Car { private Engine _engine; }`

Why favour Composition over Inheritance?
* Inheritance can lead to large, fragile hierarchies that are easy to abuse/ misuse
* Inheritance is tightly coupled

3) Inheritance

3a) Access Modifiers

Black Box Metaphor: We are incentivised to design our classes to look like black boxes, so that there is less risk when modifying it later.
If elemenents are not visible to other parts of your code, then you know you don't need to worry about them breaking when you make changes.
We want our public interface to be as simple as possible, using a literal black box like a DVD player as an example.
Few buttons/ operations, and simple ways to modify state, but a lot of complexity hidden away on the inside.

Public - Accessible from everywhere and anywhere.
Private - Accessible only from the class.
Protected - Accessible only from the class and its derived classes (not its objects). Breaks encapsulation, as derived classes should not be able to see.
Internal - Accessible only from the same assembly.
Protected Internal - Accessibly one from the same assembly or any derived classes (avoid).

3b) Constructors and Inheritance

* Base class constructors are always executed first
* Base class constructors are not inherited

In short, private members on parent classes are not available in child classes. Instead, we use the `base` keyword to access the parent (base) class.
Where Car is a sub-class of some parent Vehicle class:
`public Car(String registrationNumber) : base(registrationNumber) {}`

3c) Upcasting and Downcasting

* Conversion from a derived class to a base class is Upcasting
* Conversion from a base class to a derived class is Downcasting

Upcasting:
Circle circle = new Circle();
Shape shape = circle;

Downcasting:
Circle anotherCircle = (Circle)shape;

3d) Boxing and Unboxing

* Value types
  * Stored on the stack, and have a short liftime. Dropped whenever not in scope.
  * Examples; all primitive types (byte, int, float, char, bool), and struct
* Reference types
  * Stored in the heap, and have a longer lifetime.
  * Examples; any class (object, array, string, etc.)

Boxing: The process of converting a value type instance to an object reference.
_This creates an object in the Heap, and a reference to that object in the Stack._
`int number = 10;`
`object obj = number;`
||
`object obj = 10;`

Unboxing: The process of converting an object reference from the heap to a value type in the stack.

Both of these actions have a performance penalty.

4) Polymorphism

4a) Method Overriding

* Modifying the implementation of an inherited method.
* `virtual` keyword is used to make a method changeable in a derived class
* `override` keyword is used in the derived class to override an inherited class

4b) Abstract Classes and Members

* Used when providing common behaviour, whilst enforcing use of some design.
* Abstract classes or a members are always missing implementation.
* Abstract methods must always be part of an abstract class.
* All abstract members must be implemented.
* Abstract classes can't be instantiated.
