## C# Tips
- [Partial Classes](#partial-classes)

### Partial Classes
***Partial Classes*** are used when you need to access a class in multiple files.
```c#
// Example Partial Classes:

File 1:
namespace Foo {
  public partial class Bar {
    public Bar() {
      // Constructor
    }
    public void Foo() {
      Console.WriteLine("In Foo()");
    }
  }
}

File 2:
namespace Foo {
  public partial class Bar {
    public void Zoo() {
      Console.WriteLine("In Zoo()");
    }
  }
}

File 3:
namespace Foo {
  public void Main() {
    Bar bar = new Bar();
    Bar.Foo(); // Console prints "In Foo()"
    Bar.Zoo(); // Console prints "In Zoo()"
  }
}
```

### Abstract Classes
***Abstract Classes*** can not be instantiated. The *abstract* thing you are writing is promised to be used as a base for other implementations.
```c#
// Example Abstract Classes:

namespace Foo {
  abstract class Vehicle {
     public abstract Car() {
      // Constructor
    }
  }
  class Car : Vehicle {
    public override Car() {
      // Constructor
      // base.constructor();
    }
  }
  public void Main() {
    Car car = new Car(); // Will know about abstract methods from Vehicle
  }
}
```
