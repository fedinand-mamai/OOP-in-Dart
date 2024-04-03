import 'dart:io';

// Interface for printable objects
abstract class Printable {
  void printInfo();
}

// Base class
class Person {
  String name;
  int age;

  Person(this.name, this.age);

  void speak() {
    print('Person speaks');
  }
}

// Student class inheriting from Person and implementing Printable interface
class Student extends Person implements Printable {
  String school;

  Student(String name, int age, this.school) : super(name, age);

  @override
  void speak() {
    print('Student asks questions');
  }

  @override
  void printInfo() {
    print('Student: $name, Age: $age, School: $school');
  }
}

void main() {
  // Create an instance of Student initialized with data from a file
  Student myStudent = initializeStudentFromFile('student_data.txt');
  
  // Demonstrate the use of a loop
  for (int i = 0; i < 3; i++) {
    print('Loop iteration: $i');
  }

  // Call methods to demonstrate inheritance and overriding
  myStudent.speak();
  myStudent.printInfo();
}

// Initialize Student object from file
Student initializeStudentFromFile(String fileName) {
  File file = File(fileName);
  List<String> data = file.readAsLinesSync();

  String name = data[0];
  int age = int.parse(data[1]);
  String school = data[2];

  return Student(name, age, school);
}
