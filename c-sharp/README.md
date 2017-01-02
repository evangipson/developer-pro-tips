## C# Tips
- [Partial Classes](#partial-classes)
- [Access Modifiers](#access-modifiers)
- [Abstract Access Modifier](#abstract-access-modifier)
- [Protected Access Modifier](#protected-access-modifier)

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

### Access Modifiers
In C#, we use ***access modifiers*** to control the scope of the data. Here is a simple referencial table for all of C#'s basic access modifiers:

|Accessibility|Meaning|
|---|---|
|```public```|Access is not restricted.|
|```protected```|Access is limited to the containing class or types derived from the containing class.|
|```internal```|Access is limited to the current assembly.|
|```protected internal```|Access is limited to the current assembly or types derived from the containing class.|
|```private```|Access is limited to the containing type.|

### Abstract Access Modifier
Variables using the ***Abstract Access Modifier*** can not be instantiated. The *abstract* thing you are writing is promised to be used as a base for other implementations.
```c#
// Example Abstract Access Modifiers:

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

### Protected Access Modifier
Variables using the ***Protected Access Modifier*** are accessible within it's class and derived classes.
```c#
// Example Protected Classes:

namespace Foo {
    class Bar {
        protected int x = 123;
    }

    class Zoo : Bar {
        static void Main()
        {
            Bar bar = new Bar();
            Zoo zoo = new Zoo();

            // Error CS1540, because x can only be accessed by
            // classes derived from Bar.
            // bar.x = 10; 

            // OK, because this class derives from Bar.
            zoo.x = 10;
        }
    }
}
```
