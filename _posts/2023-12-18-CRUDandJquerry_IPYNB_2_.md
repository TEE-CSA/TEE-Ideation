---
title: CRUD and stuff
description: Our lesson on jQuery and CRUD!
type: plan
courses: {'csa': {'week': 15}}
---

## CRUD + Jquery


```python
%%HTML
<table>
    <thead>
        <th>Name</th>
        <th>Grade</th>
        <th>Favorite Color</th>
        <th>Action</th>
    </thead>
    <tbody id="result">
    </tbody>
</table>

<script>
    class Person {
        constructor(name, grade, favoriteColor) {
            this.name = name;
            this.grade = grade;
            this.favoriteColor = favoriteColor;
        }

        // Method to display a delete button for the person
        renderDeleteButton() {
            const button = document.createElement('button');
            button.textContent = 'Delete';
            button.addEventListener('click', () => {
                // Call the deletePerson function with the current person object
                deletePerson(this);
            });
            return button;
        }
    }

    // Sample people objects
    const person1 = new Person("John Doe", "A", "Blue");
    const person2 = new Person("Jane Smith", "B", "Red");
    const person3 = new Person("Bob Johnson", "C", "Green");

    // Array to store people objects
    let people = [person1, person2, person3];

    // Function to populate the table with people objects
    function populateTable() {
        const tableBody = document.getElementById('result');

        // Clear existing rows
        tableBody.innerHTML = '';

        // Loop through the people array and create a row for each person
        people.forEach(person => {
            const row = tableBody.insertRow();
            const cell1 = row.insertCell(0);
            const cell2 = row.insertCell(1);
            const cell3 = row.insertCell(2);
            const cell4 = row.insertCell(3);

            cell1.textContent = person.name;
            cell2.textContent = person.grade;
            cell3.textContent = person.favoriteColor;

            // Add the delete button to the last cell
            cell4.appendChild(person.renderDeleteButton());
        });
    }

    // Function to delete a person from the array and update the table
    function deletePerson(personToDelete) {
        people = people.filter(person => person !== personToDelete);
        populateTable();
    }

    // Call the function to initially populate the table
    populateTable();
</script>
```


<table>
    <thead>
        <th>Name</th>
        <th>Grade</th>
        <th>Favorite Color</th>
        <th>Action</th>
    </thead>
    <tbody id="result">
    </tbody>
</table>

<script>
    class Person {
        constructor(name, grade, favoriteColor) {
            this.name = name;
            this.grade = grade;
            this.favoriteColor = favoriteColor;
        }

        // Method to display a delete button for the person
        renderDeleteButton() {
            const button = document.createElement('button');
            button.textContent = 'Delete';
            button.addEventListener('click', () => {
                // Call the deletePerson function with the current person object
                deletePerson(this);
            });
            return button;
        }
    }

    // Sample people objects
    const person1 = new Person("John Doe", "A", "Blue");
    const person2 = new Person("Jane Smith", "B", "Red");
    const person3 = new Person("Bob Johnson", "C", "Green");

    // Array to store people objects
    let people = [person1, person2, person3];

    // Function to populate the table with people objects
    function populateTable() {
        const tableBody = document.getElementById('result');

        // Clear existing rows
        tableBody.innerHTML = '';

        // Loop through the people array and create a row for each person
        people.forEach(person => {
            const row = tableBody.insertRow();
            const cell1 = row.insertCell(0);
            const cell2 = row.insertCell(1);
            const cell3 = row.insertCell(2);
            const cell4 = row.insertCell(3);

            cell1.textContent = person.name;
            cell2.textContent = person.grade;
            cell3.textContent = person.favoriteColor;

            // Add the delete button to the last cell
            cell4.appendChild(person.renderDeleteButton());
        });
    }

    // Function to delete a person from the array and update the table
    function deletePerson(personToDelete) {
        people = people.filter(person => person !== personToDelete);
        populateTable();
    }

    // Call the function to initially populate the table
    populateTable();
</script>


