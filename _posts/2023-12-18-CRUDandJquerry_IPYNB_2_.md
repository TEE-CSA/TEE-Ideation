---
title: CRUD + JQUERY Connection
description: Our lesson on jQuery and CRUD!
---

<!-- Include jQuery library -->
<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>

<style>
    /* Set background color, font, and remove default margins and padding for the body */
    body {
        background-color: #a8c0ff; /* Disney Blue */
        font-family: 'Arial', sans-serif;
        margin: 0;
        padding: 0;
    }

    /* Style for the table */
    table {
        border-collapse: collapse;
        width: 100%;
        margin-top: 20px;
    }

    /* Style for table header and cells */
    th, td {
        border: 1px solid #70a9ff; /* Disney Blue */
        padding: 10px;
        text-align: left;
    }

    /* Style for table header */
    th {
        background-color: #3d5af1; /* Disney Blue */
        color: white;
    }

    /* Style for buttons */
    button {
        background-color: #3d5af1; /* Disney Blue */
        color: white;
        border: none;
        padding: 8px 12px;
        cursor: pointer;
    }

    /* Style for button hover effect */
    button:hover {
        background-color: #1c3faa; /* Lighter Disney Blue */
    }
</style>

<!-- HTML table structure with an empty tbody for dynamic data -->
<table id="data-table">
    <thead>
        <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Email</th>
        <th>Actions</th>
        </tr>
    </thead>
    <tbody>
        <!-- Data will be dynamically added here -->
    </tbody>
</table>

<!-- Button to trigger the creation of a new Disney character -->
<button id="create-btn">Create Disney Character</button>



<script>
    // Initial data for Disney characters
    const initialData = [
        { id: 1, name: 'Mickey Mouse', email: 'mickey@example.com' },
        { id: 2, name: 'Donald Duck', email: 'donald@example.com' }
    ];

    // Dynamic data that can be updated or modified
    let dynamicData = [...initialData];

    // Function to render data into the table
    function renderData(data) {
        const tableBody = $('#data-table tbody');
        tableBody.empty();

        // Loop through the data and create table rows dynamically
        data.forEach(item => {
            const row = `
                <tr>
                    <td>${item.id}</td>
                    <td>${item.name}</td>
                    <td>${item.email}</td>
                    <td>
                        <button class="update-btn" data-id="${item.id}">Update</button>
                        <button class="delete-btn" data-id="${item.id}">Delete</button>
                    </td>
                </tr>
            `;
            tableBody.append(row);
        });
    }

    // Function to create a new Disney character
    function createDisneyCharacter() {
        const newName = prompt('Enter the name of the Disney character:');
        const newEmail = prompt('Enter the email of the Disney character:');
        const newId = dynamicData.length + 1;

        // Add the new character to the dynamic data array
        dynamicData = [...dynamicData, { id: newId, name: newName, email: newEmail }];

        // Render the combined data (initial + dynamic)
        renderData([...initialData, ...dynamicData]);
    }

    // Event handler for the "Create Disney Character" button click
    $('#create-btn').on('click', createDisneyCharacter);

    // Event handler for the "Delete" and "Update" buttons inside the table
    $('#data-table').on('click', '.delete-btn', function() {
        // Get the ID of the item to delete
        const idToDelete = $(this).data('id');
        // Filter out the item with the specified ID from the dynamic data
        dynamicData = dynamicData.filter(item => item.id !== idToDelete);
        // Render the combined data (initial + dynamic)
        renderData([...initialData, ...dynamicData]);
    });

    // Event handler for the "Update" button inside the table
    $('#data-table').on('click', '.update-btn', function() {
        // Get the ID of the item to update
        const idToEdit = $(this).data('id');
        // Find the index of the item in the dynamic data array
        const updateIndex = dynamicData.findIndex(item => item.id === idToEdit);

        // Check if the item was found
        if (updateIndex !== -1) {
            // Prompt the user for the new name and email
            const updateName = prompt('Enter the new name of the Disney character:');
            const updateEmail = prompt('Enter the new email of the Disney character:');

            // Update the item in the dynamic data array
            dynamicData[updateIndex] = { id: idToEdit, name: updateName, email: updateEmail };

            // Render the combined data (initial + dynamic)
            renderData([...initialData, ...dynamicData]);
        }
    });

    // Initial rendering of the table with the initial data
    renderData([...initialData, ...dynamicData]);
</script>


