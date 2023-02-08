# <img src="https://user-images.githubusercontent.com/70295997/217401037-a4b98acb-c52c-49b4-90ed-a44b27407ea2.png" width=40> Encapsulation

_Encapsulation is one of the core concepts of Object Oriented Programming (OOP)._ Mainly, encapsulation binds together the code and data in a single unit of work (a class) and acts as a defensive shield that doesn’t allow the external code to access this data directly. _It is the technique of hiding the object state from the outer world and exposing a set of <code>public</code> methods for accessing this state. When each object keeps its state <code>private</code> inside a class, encapsulation is achieved. This is why encapsulation is also known as the **data-hiding** mechanism._

The code that takes advantage of encapsulation is:
- [x] loosely coupled (eg., I can change the names of the class variables without breaking the client code)
- [x] reusable
- [x] secure (the client is not aware of how data is manipulated inside the class)
- [x] easy to test (it’s easier to test methods than fields)

<img src="https://user-images.githubusercontent.com/70295997/216810749-64a94f9b-00ad-4d5b-b112-2baa6157bb52.png" width=40> In Java, encapsulation can be achieved via the access modifiers, <code>public</code>, <code>private</code>, and <code>protected</code>.

<img src="https://user-images.githubusercontent.com/70295997/216810799-021871c1-780a-484d-8634-690968fe9c05.png" width=40> In Python, these modifiers are called vector specifiers.

Commonly, when on object manages its own state, its state is declared via <code>private</code> variables and is accesses and/or modified via <code>public</code> methods. For example, a <code>Cat</code> class can have its own state represented by fields, such as <code>mood</code>, <code>hungry</code>, and <code>energy</code>. While the code external to the <code>Cat</code> class cannot modify any of these fields directly, it can call <code>public</code> methods, such as <code>play()</code>, <code>feed()</code> and <code>sleep()</code> that modify the <code>Cat</code> state internally. The <code>Cat</code> class may also have <code>private</code> methods that are not accessible outside the class, such as <code>meow()</code>. 

<img src="https://user-images.githubusercontent.com/70295997/217401305-9cb67ac3-355c-443c-9318-0e5b9d3d64b1.png" width=40> This is encapsulation.

<img src="https://user-images.githubusercontent.com/70295997/216810749-64a94f9b-00ad-4d5b-b112-2baa6157bb52.png" width=40> [Java code sample](https://github.com/lana-20/oop-encapsulation/blob/main/java-class-cat):

    public class Cat {

      private int mood = 50;
      private int hungry = 50;
      private int energy = 50;

      public void sleep() {
        System.out.println(“Sleep …”);
        energy ++;
        hungry ++;
      }

      public void play() {
        System.out.println(“Play …”);
        mood ++;
        energy --;
        meow();
      }

      public void feed() {
        System.out.println(“Feed …”);
        hungry --;
        mood ++;
        meow();
      }

      private void meow() {
        System.out.println(“Meow …”);
      }

      public int getMood() {
        return mood;
      }

      public int getHungry() {
        return hungry;
      }

      public int getEnergy() {
        return energy;
      }
    }

The only way to modify the state is via the public methods, play(), feed(), and sleep().

    public static void main(String[] args) {

      Cat cat = new Cat();

      cat.feed();
      cat.play();
      cat.feed();
      cat.sleep();

      System.out.println(“Energy: ” + cat.getEnergy());
      System.out.println(“Mood: ” + cat.getMood());
      System.out.println(“Hungry: ” + cat.getHungry());
    }

The output is as follows:

    Feed …Meow!Play …Meow!Feed …Meow!Sleep …

    Energy: 50
    Mood: 53
    Hungry: 49

<img src="https://user-images.githubusercontent.com/70295997/216810799-021871c1-780a-484d-8634-690968fe9c05.png" width=40> Here's the Python equivalent of the Java code, using Python property decorators to demonstrate encapsulation in Object Oriented Programming:

    class Cat:
        def __init__(self):
            self._mood = 50
            self._hungry = 50
            self._energy = 50

        def sleep(self):
            print("Sleep…")
            self._energy += 1
            self._hungry += 1

        def play(self):
            print("Play…")
            self._mood += 1
            self._energy -= 1
            self._meow()

        def feed(self):
            print("Feed…")
            self._hungry -= 1
            self._mood += 1
            self._meow()

        def _meow(self):
            print("Meow…")

        @property
        def mood(self):
            return self._mood

        @property
        def hungry(self):
            return self._hungry

        @property
        def energy(self):
            return self._energy

    if __name__ == "__main__":
        cat = Cat()

        cat.feed()
        cat.play()
        cat.feed()
        cat.sleep()

        print("Energy:", cat.energy)
        print("Mood:", cat.mood)
        print("Hungry:", cat.hungry)

The output is as follows:

    Feed…
    Meow…
    Play…
    Meow…
    Feed…
    Meow…
    Sleep…
    Energy: 51
    Mood: 52
    Hungry: 52

In this implementation, the <code>mood</code>, <code>hungry</code>, and <code>energy</code> fields are declared as protected using the leading underscore notation. The <code>get_mood()</code>, <code>get_hungry()</code>, and <code>get_energy()</code> methods are replaced with Python property getters (declared using the @property decorator).

This way, the internal state of the <code>Cat</code> object can be accessed using the properties (eg., <code>cat.energy</code>), but the underlying fields cannot be directly modified.
