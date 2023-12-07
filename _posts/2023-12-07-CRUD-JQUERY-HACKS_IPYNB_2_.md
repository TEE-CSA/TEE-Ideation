---
title: JQUERY & CRUD HACKS
description: hacks for CRUD with JQUERY
author: Tay K., Emaad M., Ethan T., Finn C., Theo H., Justin N.
comments: True
---

# Directions

- You really should try to answer the 5 questions below this without any help. These are core concepts that you should at least attempt to learn.
- The update JQUERY function may require a little help but try without first
- Hacks should only take 20 minutes at most

# Free Response and MCQ

1. What does CRUD stand for?
    - Create
    - R...
    - U
    - D

2. What are the HTTP verbs that are associated with each CRUD action?
    - C - POST
    - R
    - U
    - D

3. What is JQuery?

4. Match A, B, and C into the JQuery event handler for a data table
    - A: 'click'
    - B: '.delete-btn'
    - C: '#data-table'

    $(???).on(???, ???, function() {
    // code
  });

5. Why do we use JQUERY with CRUD?

# Finish the update JQUERY function
- its all the way at the end, you should see the green comment
- you can choose to use the two lines I've already given or not

<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
<style>
  body {
    background-color: #ffe1f4; /* Barbie Pink */
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
  }

  table {
    border-collapse: collapse;
    width: 100%;
    margin-top: 20px;
  }

  th, td {
    border: 1px solid #e66b8f; /* Barbie Pink */
    padding: 10px;
    text-align: left;
  }

  th {
    background-color: #ff8bbd; /* Barbie Pink */
    color: white;
  }

  button {
    background-color: #ff8bbd; /* Barbie Pink */
    color: white;
    border: none;
    padding: 8px 12px;
    cursor: pointer;
  }

  button:hover {
    background-color: #e66b8f; /* Lighter Barbie Pink */
  }
</style>


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

<button id="create-btn">Create Barbie Character</button>

<script>
  const initialData = [
    { id: 1, name: 'Barbie', email: 'barbie@example.com' },
    { id: 2, name: 'Ken', email: 'ken@example.com' }
  ];

  function renderData(data) {
    const tableBody = $('#data-table tbody');
    tableBody.empty();

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

  function createBarbieCharacter() {
    const newName = prompt('Enter the name of the Barbie character:');
    const newEmail = prompt('Enter the email of the Barbie character:');
    const newId = initialData.length + 1;
    
    const newData = [...initialData, { id: newId, name: newName, email: newEmail }];
    renderData(newData);
  }

  $('#create-btn').on('click', createBarbieCharacter);

  $('#data-table').on('click', '.delete-btn', function() {
    const idToDelete = $(this).data('id');
    const newData = initialData.filter(item => item.id !== idToDelete);
    renderData(newData);
  });

  $('#data-table').on('click', '.update-btn', function() {
    const idToEdit = $(this).data('id');
    const updateIndex = initialData.findIndex(item => item.id === idToEdit);

    // HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS HACKS 

    // FINISH THIS PART
    // UPDATE
  });


  // Initial rendering
  renderData(initialData);
</script>

