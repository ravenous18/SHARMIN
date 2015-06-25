Object Oriented Concepts
Before we go in detail, lets define important terms related to Object Oriented Programming.
Class: This is a programmer-defined datatype, which includes local functions as well as local data. You can think of a class as a template for making many instances of the same kind (or class) of object.
Object: An individual instance of the data structure defined by a class. You define a class once and then make many objects that belong to it. Objects are also known as instance.
Member Variable: These are the variables defined inside a class. This data will be invisible to the outside of the class and can be accessed via member functions. These variables are called attribute of the object once an object is created.
Member function: These are the function defined inside a class and are used to access object data.
Inheritance: When a class is defined by inheriting existing function of a parent class then it is called inheritance. Here child class will inherit all or few member functions and variables of a parent class.
Parent class: A class that is inherited from by another class. This is also called a base class or super class.
Child Class: A class that inherits from another class. This is also called a subclass or derived class.
Polymorphism: This is an object oriented concept where same function can be used for different purposes. For example function name will remain same but it make take different number of arguments and can do different task.
Overloading: a type of polymorphism in which some or all of operators have different implementations depending on the types of their arguments. Similarly functions can also be overloaded with different implementation.
Data Abstraction: Any representation of data in which the implementation details are hidden (abstracted).
Encapsulation: refers to a concept where we encapsulate all the data and member functions together to form an object.
Constructor: refers to a special type of function which will be called automatically whenever there is an object formation from a class.
Destructors: refers to a special type of function which will be called automatically whenever an object is deleted or goes out of scope.

Defining PHP Classes
The general form for defining a new class in PHP is as follows:
<?php
class phpClass{
   var $var1;
   var $var2 = "constant string";
   function myfunc ($arg1, $arg2) {
      [..]
   }
   [..]
}
?>

Creating Objects in PHP
Once you defined your class, then you can create as many objects as you like of that class type. Following is an example of how to create object using new operator.
$physics = new Books;
$maths = new Books;
$chemistry = new Books;

Calling Member Functions
After creating your objects, you will be able to call member functions related to that object. One member function will be able to process member variable of related object only.

Following example shows how to set title and prices for the three books by calling member functions.

$physics->setTitle( "Physics for High School" );
$chemistry->setTitle( "Advanced Chemistry" );
$maths->setTitle( "Algebra" );

$physics->setPrice( 10 );
$chemistry->setPrice( 15 );
$maths->setPrice( 7 );
Now you call another member functions to get the values set by in above example:
$physics->getTitle();
$chemistry->getTitle();
$maths->getTitle();
$physics->getPrice();
$chemistry->getPrice();
$maths->getPrice();


Constructor Functions
Constructor Functions are special type of functions which are called automatically whenever an object is created. So we take full advantage of this behaviour, by initializing many things through constructor functions.
PHP provides a special function called __construct() to define a constructor. You can pass as many as arguments you like into the constructor function.
Following example will create one constructor for Books class and it will initialize price and title for the book at the time of object creation.
function __construct( $par1, $par2 ){
   $this->price = $par1;
   $this->title = $par2;
}

Destructor
Like a constructor function you can define a destructor function using function __destruct(). You can release all the resourceses with-in a destructor.

Inheritance
PHP class definitions can optionally inherit from a parent class definition by using the extends clause. The syntax is as follows:

class Child extends Parent {
     <definition body>
  }
  
  Function Overriding
Function definitions in child classes override definitions with the same name in parent classes. In a child class, we can modify the definition of a function inherited from parent class.

In the follwoing example getPrice and getTitle functions are overriden to retrun some values.

function getPrice(){
       echo $this->price . "<br/>";
       return $this->price;
    }
function getTitle(){
       echo $this->title . "<br/>";
       return $this->title;
}
Public Members
Unless you specify otherwise, properties and methods of a class are public. That is to say, they may be accessed in three possible situations:

From outside the class in which it is declared

From within the class in which it is declared

From within another class that implements the class in which it is declared

Till now we have seen all members as public members. If you wish to limit the accessibility of the members of a class then you define class members as private or protected.

Private members
By designating a member private, you limit its accessibility to the class in which it is declared. The private member cannot be referred to from classes that inherit the class in which it is declared and cannot be accessed from outside the class.

A class member can be made private by using private keyword infront of the member.

class MyClass {
   private $car = "skoda";
   $driver = "SRK";

   function __construct($par) {
      // Statements here run every time
      // an instance of the class
      // is created.
   }
   function myPublicFunction() {
      return("I'm visible!");
   }
   private function myPrivateFunction() {
      return("I'm  not visible outside!");
   }
}
When MyClass class is inherited by another class using extends, myPublicFunction() will be visible, as will $driver. The extending class will not have any awareness of or access to myPrivateFunction and $car, because they are declared private.

Protected members
A protected property or method is accessible in the class in which it is declared, as well as in classes that extend that class. Protected members are not available outside of those two kinds of classes. A class member can be made protected by using protected keyword infront of the member.

Here is different version of MyClass:

class MyClass {
   protected $car = "skoda";
   $driver = "SRK";

   function __construct($par) {
      // Statements here run every time
      // an instance of the class
      // is created.
   }
   function myPublicFunction() {
      return("I'm visible!");
   }
   protected function myPrivateFunction() {
      return("I'm  visible in child class!");
   }
}
Interfaces
Interfaces are defined to provide a common function names to the implementors. Different implementors can implement those interfaces according to theri requirements. You can say, interfaces are skeltons which are implemented by developers.

As of PHP5, it is possible to define an interface, like this:

interface Mail {
   public function sendMail();
}
Then, if another class implemented that interface, like this:

class Report implements Mail {
   // sendMail() Definition goes here
}
Constants
A constant is somewhat like a variable, in that it holds a value, but is really more like a function because a constant is immutable. Once you declare a constant, it does not change.

Declaring one constant is easy, as is done in this version of MyClass:

class MyClass {
   const requiredMargin = 1.7;
   function __construct($incomingValue) {
      // Statements here run every time
      // an instance of the class
      // is created.
   }
}
In this class, requiredMargin is a constant. It is declared with the keyword const, and under no circumstances can it be changed to anything other than 1.7. Note that the constant's name does not have a leading $, as variable names do.

Abstract Classes
An abstract class is one that cannot be instantiated, only inherited. You declare an abstract class with the keyword abstract, like this:

When inheriting from an abstract class, all methods marked abstract in the parent's class declaration must be defined by the child; additionally, these methods must be defined with the same visibillity.

abstract class MyAbstractClass {
   abstract function myAbstractFunction() {
   }
}
Note that function definitions inside an abstract class must also be preceded by the keyword abstract. It is not legal to have abstract function definitions inside a non-abstract class.

Static Keyword
Declaring class members or methods as static makes them accessible without needing an instantiation of the class. A member declared as static can not be accessed with an instantiated class object (though a static method can).

Try out following example:

<?php
class Foo
{
    public static $my_static = 'foo';

    public function staticValue() {
        return self::$my_static;
    }
}
print Foo::$my_static . "\n";
$foo = new Foo();
print $foo->staticValue() . "\n";
Final Keyword
PHP 5 introduces the final keyword, which prevents child classes from overriding a method by prefixing the definition with final. If the class itself is being defined final then it cannot be extended.

Following example results in Fatal error: Cannot override final method BaseClass::moreTesting()

<?php
class BaseClass {
   public function test() {
       echo "BaseClass::test() called<br>";
   }
  
   final public function moreTesting() {
       echo "BaseClass::moreTesting() called<br>";
   }
}

class ChildClass extends BaseClass {
   public function moreTesting() {
       echo "ChildClass::moreTesting() called<br>";
   }
}
?>
Calling parent constructors
Instead of writing an entirely new constructor for the subclass, let's write it by calling the parent's constructor explicitly and then doing whatever is necessary in addition for instantiation of the subclass. Here's a simple example:

class Name
{
   var $_firstName;
   var $_lastName;
   function Name($first_name, $last_name)
   {
     $this->_firstName = $first_name;
     $this->_lastName = $last_name;
   }
   function toString() {
     return($this->_lastName .", " .$this->_firstName);
   }
}
class NameSub1 extends Name
{
   var $_middleInitial;
   function NameSub1($first_name, $middle_initial, $last_name) {
       Name::Name($first_name, $last_name);
       $this->_middleInitial = $middle_initial;
   }
   function toString() {
       return(Name::toString() . " " . $this->_middleInitial);
   }
}
In this example, we have a parent class (Name), which has a two-argument constructor, and a subclass (NameSub1), which has a three-argument constructor. The constructor of NameSub1 functions by calling its parent constructor explicitly using the :: syntax (passing two of its arguments along) and then setting an additional field. Similarly, NameSub1 defines its nonconstructor toString() function in terms of the parent function that it overrides.
