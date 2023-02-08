# Encapsulation

Encapsulation is one of the core concepts of Object Oriented Programming (OOP). Mainly, encapsulation binds together the code and data in a single unit of work (a class) and acts as a defensive shield that doesn’t allow the external code to access this data directly. It is the technique of hiding the object state from the outer world and exposing a set of public methods for accessing this state. 

When each object keeps its state private inside a class, encapsulation is achieved. This is why encapsulation is also known as the data-hiding mechanism. The code that takes advantage of encapsulation is:
- [x] loosely coupled (eg., I can change the names of the class variables without breaking the client code)
- [x] reusable
- [x] secure (the client is not aware of how data is manipulated inside the class)
- [x] easy to test (it’s easier to test methods than fields)

In Java, encapsulation can be achieved via the access modifiers, public, private, and protected. 
In Python, these are called vector specifiers.

Commonly, when on object manages its own state, its state is declared via private variables and is accesses and/or modified via public methods. For example, a Cat class can have its own state represented by fields, such as mood, hungry, and energy. While the code external to the Cat class cannot modify any of these fields directly, it can call public methods, such as play(), feed() and sleep() that modify the Cat state internally. The Cat class may also have private methods that are not accessible outside the class, such as meow(). 

This is encapsulation.

Java code sample:

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

    public static main void (String[] args) {

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
