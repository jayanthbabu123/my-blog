+++
title = 'Javascript Todo List Assignment'
date = 2024-04-19T15:06:48+05:30
draft = false
+++

# JavaScript Exercise: Todo List

**Description:**

Create a simple todo list application using HTML, CSS, and JavaScript. The application should include an input box and an "Add" button. When the user enters text into the input box and clicks "Add", the text should be added as a new item in an initially empty unordered list. Each new todo item should be accompanied by two buttons: a "Complete" button and a "Delete" button. Clicking the "Complete" button should strike through the todo item, indicating that it has been completed. Clicking the "Delete" button should remove the item from the list entirely. The application should prevent the addition of empty items; if the input box is empty when the "Add" button is clicked, no new item should be added to the list.

**Expected Output:**

- An input field with an adjacent "Add" button to submit new todo items.
- An empty unordered list that gets populated with new items entered through the input field.
- Each list item has a "Complete" button that, when clicked, strikes through the item text.
- Each list item has a "Delete" button that, when clicked, removes the item from the list.
- Empty values should not be added to the list; the application should ensure only non-empty entries are added as items.

# Demo

<h1>Todo List</h1>
    <input type="text" id="todoInput" placeholder="Add a new todo...">
    <button id="addButton">Add</button>
    <ul id="todoList"></ul>

  <style>
#todoInput {
            margin-right: 10px;
            width: 50%;
    height: 30px;
    padding: 10px;
    box-sizing: border-box;
    border-radius: 5px;
    font-size: 15px;
        }
        #todoList {
            list-style-type: none;
            padding: 0;
        }
        #todoList li {
            margin-bottom: 10px;
        }
        .completed {
            text-decoration: line-through;
        }
        .button{
             margin-left: 10px;
            cursor: pointer;
            border-radius: 5px;
        }
         #addButton {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 7px 30px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            margin-left: 10px;
            cursor: pointer;
            border-radius: 5px;
        }
    </style>
<script>
        const addButton = document.getElementById('addButton');
        const todoList = document.getElementById('todoList');
        const todoInput = document.getElementById('todoInput');

        addButton.addEventListener('click', function() {
            const text = todoInput.value.trim();
            if (text !== '') {
                const li = document.createElement('li');
                li.textContent = text;

                const completeButton = document.createElement('button');
                completeButton.textContent = 'Complete';
                completeButton.className = 'button';
                completeButton.onclick = function() {
                    li.classList.toggle('completed');
                };

                const deleteButton = document.createElement('button');
                deleteButton.textContent = 'Delete';
                deleteButton.className = 'button';
                deleteButton.onclick = function() {
                    todoList.removeChild(li);
                };

                li.appendChild(completeButton);
                li.appendChild(deleteButton);
                todoList.appendChild(li);

                todoInput.value = '';  // Clear the input box after adding
            }
        });
</script>
