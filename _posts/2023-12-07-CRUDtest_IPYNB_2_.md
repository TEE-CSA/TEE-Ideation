---
title: CRUD Principles
description: learn crud
type: plan
courses: {'csa': {'week': 15}}
---

# What is CRUD?

**Create (C):**

GOAL: create records or objects in a database, like creating records in SQLITE database in SPRING java project. 

**Read (R):**

GOAL: retrieve data from our database for display or for interaction

**Update (U):**

GOAL: Update our data in our database, such as changing attributes like name

**Delete (D):**

GOAL: remove data from our database, like removing objects from our database

### popcorn hack

talk about usage of one of four elements of CRUD from your project in tri 1. Focus on how CRUD was implemented. 

### simple example of CRUD


```Java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
class Person {
    private int id;
    private String name;
    public Person(int id, String name) {this.id = id; this.name = name;}
    public int getId() {return id;}
    public String getName() {return name;}
    public void setName(String name) {this.name = name;}
}
public class CrudExample {
    private static List<Person> people = new ArrayList<>();
    private static int nextId = 1;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (true) { System.out.println("1. Create\n2. Read\n3. Update\n4. Delete\n5. Exit\nEnter your choice: ");
            int choice = scanner.nextInt();
            switch (choice) {
                case 1: createPerson(scanner); break;
                case 2: readPeople(); break;
                case 3: updatePerson(scanner); break;
                case 4: deletePerson(scanner); break;
                case 5: System.out.println("Exiting program."); return;
                default: System.out.println("Invalid choice. Please try again.");
            }
        }
    }
    //CREATE
    private static void createPerson(Scanner scanner) {
        System.out.print("Enter person name: "); String name = scanner.next();
        Person person = new Person(nextId++, name); people.add(person);
        System.out.println("Person created with ID: " + person.getId());
    }
    //READ
    private static void readPeople() {
        System.out.println("People:");
        for (Person person : people) {System.out.println("ID: " + person.getId() + ", Name: " + person.getName());}
    }
    //UPDATE
    private static void updatePerson(Scanner scanner) {
        System.out.print("Enter person ID to update: "); int idToUpdate = scanner.nextInt();
        for (Person person : people) {if (person.getId() == idToUpdate) {System.out.print("Enter new name: "); String newName = scanner.next(); person.setName(newName); System.out.println("Person updated successfully."); return;}}
        System.out.println("Person with ID " + idToUpdate + " not found.");
    }
    //DELETE 
    private static void deletePerson(Scanner scanner) {
        System.out.print("Enter person ID to delete: "); int idToDelete = scanner.nextInt();
        for (Person person : people) {if (person.getId() == idToDelete) {people.remove(person); System.out.println("Person deleted successfully."); return;}}
        System.out.println("Person with ID " + idToDelete + " not found.");
    }
}
CrudExample.main(null);
```

    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    Enter person name: Person created with ID: 1
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    People:
    ID: 1, Name: foipfifhiw
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    Enter person ID to update: Enter new name: Person updated successfully.
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    People:
    ID: 1, Name: test
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    Enter person ID to delete: Person deleted successfully.
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    People:
    1. Create
    2. Read
    3. Update
    4. Delete
    5. Exit
    Enter your choice: 
    Exiting program.

