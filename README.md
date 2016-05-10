# Java Data Structures
## ArrayLists, HashMaps, Classes

### Objective
Know: Java data structures
Show: An ArrayList of a custom class
Level of Thinking: Comprehension

### ArrayLists
### Why ArrayLists?
ArrayLists are more flexible than arrays, and have methods that can be called outside the static class.
Let's say we have a list of students. We could hold these in a String[], but what if a student drops? Or adds the class? We need to be able to dynamically work with the array of items in a way that Java Arrays do not allow.
### What is an ArrayList?
Just like arrays, arrayLists can hold one type. They are written like so:

    ArrayList<String> strings = new ArrayList<>();

Some common methods are:

1. boolean strings.add("new string");
1. void strings.clear();
1. boolean strings.remove(index OR "new string")
1. boolean strings.contains("new string");
1. int strings.indexOf("new string");
1. int strings.size();

### ArrayList Practice
Take the following list of names and add them to a new ArrayList<String>:

Temika Berthiaume  
Karan Withrow  
Tonja Fitting  
April Fronk  
Marylouise Haake

Let's loop through the names to make sure they all got added correct:

    System.out.println("----After Inital Add----");
    for(String student : students) {
      System.out.println(student);
    }
    
When you run this, you should see all 5 names.

Now add a few more names using the add method. Remove the name at [4]. Then remove "Karen Withrow" without using the index.  Check to see if the removals happened like you expected.

    System.out.println("----After more adding removal----");
    for(String student : students) {
      System.out.println(student);
    }

### HashMaps
#### Why HashMaps?
ArrayLists are great, but what if you we want to assign an ID to each of our students? We can't do that with a array of values.
#### What is a HashMap?
HashMaps are a way to store two values mapped to each other, sort of like the key, value pair in a JavaScript object.
HashMaps are created like this:

    HashMap<Integer, String> students = new HashMap<>();
    
Notice that the type of each element needs to be defined when you create the HashMap. The HashMap above will only hold pairs of Integers and Strings. However, you could make a new HashMap<Boolean, Integer> or HashMap<String, String>. The sky is the limit, as we shall see soon!

Some common useful methods on HashMaps are:
1. boolean students.put(1, "Temika Berthiaume")
2. <value's type> students.get(key) so in this case: students.get(1)
3. <value> students.remove(key)
4. <old value> students.replace(key, newValue)
5. boolean students.containsKey(key)
6. boolean students.containsValue(value)
7. int students.size();

#### HashMaps Practice
Create a HashMap of your students, each with an incrementing ID number.
Let's loop through your HashMap and output the student names. This is a bit more complicated.

    System.out.println("----Student HashMap----");
    for (String student : studentMap.values()) {
      System.out.println(student);
    }

Java also supports a lot of the higher order functions you are used to but you won't see them as widely used as the format above.

    System.out.println("----Student HashMap (foreach)----");
    studentMap.values().forEach(student -> {
      System.out.println(student);
    });

### Classes
### Why classes?
First, they're the backbone of Java. You can do nearly anything you want to do with a class. You will recognize their structure from our early lesson on Object-Oriented Design. Java is a purely Object-Oriented language, so the wonky stuff we were trying to cram into JavaScript then will make much more sense as we learn more about Java.
Second, for our purposes today, a class will let us hold any information about our students that we want. Right now we can store an ID and a name, but what if we wanted to access their first name and last name separately? Or add any other data? HashMaps are still limited in that they can pretty much only hold one key and value set. They're not great for modeling a complex object.
### What is a class?
A Java class that we would write is basically a custom object. There is some really important accepted syntax around most classes in Java. This includes setting the properties of the class as private, and then making getters and setters for each. Classes usually have a constructor method as well, for making new instantiations of the class. A student class would probably look like this:

    public class Student {
      // private properties are declared
      private int id;
      private String firstName;
      private String lastName;

      // constructor
      public Student (int id, String firstName, String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
      }

      // getter and setter for id and firstName. The same would be written for all the properties. IDEs will usually do this for you.
      public int getId () {
        return this.id;
      }

      public void setId (int id) {
        this.id = id;
      }

      public String getFirstName () {
        return this.firstName;
      }

      public void setFirstName (String firstName) {
        this.firstName = firstName;
      }

      ...
    }

Java is verbose!

We can also add methods other than getters and setters to our student. For example, we could add a method to get their full name.

    public String getFullName () {
      return this.firstName + " " + this.lastName;
    }
Drop that into the Student class and we can get their full name now!

#### Using Classes
Finish writing the getter and setter for our Student class above.

Now we need to actually use our Student class to make a new student. This is done like so:

    Student temika = new Student(1, "Temika", "Berthiaume");

Now that we have that student, we could call any of the methods we wrote into the class for her, like:

    String fullName = temika.getFullName();

### ArrayList of a Class
Great, so now we have a class that holds all kinds of complex information about a student. Remember earlier when we said that the sky was the limit on the other data structures? Well, now we can keep a list of our students, with all their info, like this:

    ArrayList<Student> students = new ArrayList<>();
    students.put(temika);

So that's cool. But you can even instantiate right there in the list:

    students.put(new Student(2, "Karan", "Withrow"));

Sweet!
That's a list that holds a bunch of Students instead of Strings. We could do the same with HashMaps, like HashMap<int, Student>, that might store their grade and their profile.
