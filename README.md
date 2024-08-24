# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

After completing this lab, I was able to:

Create a simple Todo List application using React and add headings and associated lists to organize tasks.

Manage the todo items ans delete specific headings and lists, provide basic CRUD (Create, Read, Update, Delete) functionality.

Use React's useState hook to manage the state of the Todo List, including the list of headings and associated lists.

Use React's useState hook also to render the values dynamically.


Lab: Todo List Application
 


Estimated time needed: 40 minutes
What you will learn
In this lab, you will learn how to use React functional components and the useState hook to make a simple to-do list application. You will learn how to manage state using the useState hook. The lab includes the basics of managing React states, taking user input, and showing dynamic lists of things.
Learning objectives
After completing this lab, you will be able to:
•	Create a simple Todo List application using React and add headings and associated lists to organize tasks.
•	Manage the todo items ans delete specific headings and lists, provide basic CRUD (Create, Read, Update, Delete) functionality.
•	Use React's useState hook to manage the state of the Todo List, including the list of headings and associated lists.
•	Use React's useState hook also to render the values dynamically.
Prerequisites
•	Basic knowledge of HTML
•	Intermediate knowledge of JavaScript
•	Basic knowledge of React functional component and state management using useState hook
Setting up the environment
1.	From the menu on top of the lab, click the Terminal tab at the top-right of the window shown at number 1 in the given screenshot, and then click New Terminal as shown at number 2.
 
2.	Now, write the following command in the terminal to clone the boiler template for this React application and hit Enter.
1.	1
1.	git clone https://github.com/ibm-developer-skills-network/todo_list.git
Copied!
3.	The above command will create a folder, "todo_list" under the "Project" folder. You can see the structure in the screenshot.
 
4.	Next, you need to run the React application by entering the folder name in the terminal using the given command. This action will set your terminal path to run the React application within the todo_list folder.
1.	1
ii.	cd todo_list
Copied!
5.	To ensure the code you have cloned is working correctly, you need to perform the following steps:
o	Write the given command in the terminal and hit Enter. This command will install all the necessary packages to execute the application.
1.	1
b.	npm install
Copied!
o	Then execute the following command to run the application and this will provide you with port number 4173.
1.	1
b.	npm run preview
Copied!
6.	To view your React application, click the Skills Network icon on the left (refer to number 1). This action will open the SKILLS NETWORK TOOLBOX. Next, click Launch Application (refer to number 2). Enter the port number 4173 in Application Port (refer to number 3) and click  .
 
7.	The output will display as shown in the given screenshot.
 
8.	You can preserve your latest work on this lab by adding, committing, and pushing it to your GitHub repository. This ensures that even if you’re not working on the task continuously, your progress will be saved, allowing you to resume from where you left off.
Note: Step 8 is optional.

Setting the initial state
1.	Next, navigate to the TodoList.jsx file located in the Components folder of the src directory in your cloned todo_list folder.
2.	The basic structure of this component will be as shown in the screenshot.
 
•	The above code represents the basic structure of a todo list component in a React application. It includes a container for the todo list <div className="todo-container"> with a title "My Todo List" and an input container <div className="input-container"> containing an input field for entering todo headings and a button labeled "Add Heading".
•	There is a main section <div className="todo_main"> intended to display the todo items. You need to apply the functionality for handling user input, managing todo items, and dynamically rendering them, which would be implemented using React state and event handling.
•	You need to initialize the following three states:
o	todos: To represent an array of todo items. Initialize it with an empty array [], indicating that there are no todo items initially.
o	headingInput: To represent the value entered by user into an input field for adding a new heading for a todo item. Initialize it as an empty string ''.
o	listInputs: Initialize listInputs as an empty object {}. This state will hold the value of input fields for each todo item individually.
4.	1
5.	2
6.	3
vii.	  const [todos, setTodos] = useState([]);
viii.	  const [headingInput, setHeadingInput] = useState('');
ix.	  const [listInputs, setListInputs] = useState({});
Copied!
Note: Include above code before return of component.

Implement Add Heading Functionality:
Add Heading Functionality for Todo List
•	At first, for the similar todo tasks you will add the specific heading such as Grocery Items. Under this heading, list todo items will come like milk, butter, and bread.
•	For this one input tag has already been provided to you with class name heading-input. To get the heading from this input box, you need to create a function named as handleAddTodo that will be triggered on clicking the Add Heading button.
•	Check if headingInput is empty. If not empty, create a new todo object with the heading from headingInput and an empty array for lists.
•	Then append this todo object to the todo array and clear headingInput by setting it to an empty string.
1.	1
2.	2
3.	3
4.	4
5.	5
6.	6
vii.	  const handleAddTodo = () => {
viii.	    if (headingInput.trim() !== '') {
ix.	      setTodos([...todos, { heading: headingInput, lists: [] }]);
x.	      setHeadingInput('');
xi.	    }
xii.	  };
Copied!
In the above code:
o	const handleAddTodo = () => { ... }: Declares a constant named handleAddTodo and assigns it an arrow function.
o	if (headingInput.trim() !== '') { ... }: Checks if the headingInput variable, a piece of text input from the user, is empty after trimming any whitespace characters from the beginning and end. This condition ensures that the user has entered some content before proceeding.
o	setTodos([...todos, { heading: headingInput, lists: [] }]);: If the condition in the if statement is met, this line updates the state variable todos. It spreads the existing todos array (todos) into a new array using the spread syntax (…todos) and appends a new object to it. The new object contains a heading property set to the value of headingInput and a lists property initialized as an empty array.
o	setHeadingInput('');: After adding a new todo item, this line clears the headingInput state variable, resetting the text input field for the user to enter a new todo item heading.
Note: Include above code after initializing the three states.
o	To implement the "Add Todo" functionality, changes need to be made inside the div tag with classname input-container where the input field and the button for adding the heading are located.
o	The input field and the button element in the div tag need to be updated to incorporate the functionality to add a new todo item on button click.
19.	1
20.	2
21.	3
22.	4
23.	5
24.	6
25.	7
26.	8
27.	9
28.	10
xxix.	  <div className="input-container">
xxx.	  <input
xxxi.	    type="text"
xxxii.	    className="heading-input"
xxxiii.	    placeholder="Enter heading"
xxxiv.	    value={headingInput}
xxxv.	    onChange={(e) => {setHeadingInput(e.target.value);}} // Add onChange event handler to update headingInput state
xxxvi.	  />
xxxvii.	  <button className="add-list-button" onClick={handleAddTodo}>Add Heading</button>
xxxviii.	</div>
Copied!
In the input element:
•	value attribute is set to {headingInput}, which binds the value of the 'input' field to the 'headingInput' state variable.
•	onChange: This is an event handler in React that triggers when the value of an input element changes.
o	(e) => {…}: This is an arrow function, which is a concise way to define a function in JavaScript. It takes an event (e) as an argument, which represents the event that triggered the handler.
o	{setHeadingInput(e.target.value);}: This is the body of the arrow function. Here, setHeadingInput is likely a function that updates the state variable headingInput in the component. e.target.value retrieves the current value of the input element that triggered the event, and setHeadingInput is called with this value to update the state.
In the button element:
•	onClick event handler is added to trigger the handleAddTodo function on button click. This function adds a new todo item under the entered heading.
Display Todo Heading
•	To display the heading of each todo item, you need to iterate over the todos array and render the heading within the JSX.
•	You need to update the JSX portion where each todo item is rendered inside div with class name todo-card to display the heading.
•	You need to include this code within the div tag with class name todo_main.
1.	1
2.	2
3.	3
4.	4
5.	5
6.	6
7.	7
8.	8
1.	{todos.map((todo, index) => (
2.	    <div key={index} className="todo-card">
3.	      <div className="heading_todo">
4.	        <h3>{todo.heading}</h3> {/* Display the heading here */}
5.	        <button className="delete-button-heading">Delete Heading </button>
6.	      </div>
7.	    </div>
8.	  ))}
Copied!
•	In the code:
o	Mapping over Todos Array: todos.map((todo, index) => ...): Maps over the todos array, which contains todo items.The map() function executes the specified function for each todo item in the array.
o	Rendering Todo Item: <div key={index} className="todo-card"> ... </div>: For each todo item, a div element with the class todo-card is rendered. The key attribute is set to index to identify each to-do item within the list uniquely.
o	Displaying Todo Heading: <h3>{todo.heading}</h3>: Within each todo-card div, the heading of the current todo item is displayed using an <h3> element. The heading text is retrieved from the heading property of the todo object.
o	Deleting Todo Item: <button className="delete-button-heading" onClick={() => handleDeleteTodo(index)}>Delete Heading </button>: Each todo item is accompanied by a "Delete Heading" button. When clicked, this button triggers the handleDeleteTodo function, passing the index of the current todo item as an argument. The index allows the function to identify and delete the corresponding todo item from the todos array.
•	Now save the TodoList.jsx component and re-run the application to check the working of the code. If your application is already open then just refresh the webpage.
•	Now enter the heading such as Grocery Item in the input box and click on Add Heading button. You will look output similar to given screenshot.
 
Delete Heading With Todo List
•	To delete the heading section, the entire todo list will also be deleted. Suppose if a user has entered the heading as Grocery List and all items under this heading have been added, then the user should be able to delete tthe entire list from their application interface.
•	To delete the list create a function with name handleDeleteTodo and apply logic to delete the element.
1.	5
ii.	const handleDeleteTodo = (index) => {
iii.	   const newTodos = [...todos];
iv.	   newTodos.splice(index, 1);
v.	   setTodos(newTodos);
vi.	 };
Copied!
•	The function handleDeleteTodo is designed to remove a todo item from the todos array at a specific index in the above code as follows:
o	const handleDeleteTodo = (index) => { ... }: Declares a constant named handleDeleteTodo that has an arrow function which takes an index parameter, indicating the index of the todo item to be deleted.
o	const newTodos = [...todos];: Creates a shallow copy of the todos array using the spread syntax (…todos). This step is crucial to avoid directly mutating the original state.
o	newTodos.splice(index, 1);: The splice method is called on the newTodos array to remove one element at the specified index.
o	setTodos(newTodos);: Finally, the setTodos function, provided by React's useState hook, is called with the updated newTodos array as an argument. This updates the state variable todos with the modified array, removing the todo item specified by the index from the UI and re-rendering the component accordingly.
Note: Include above code before the returnof component.
•	Now you need to include onClick event in the button with class name delete-button-heading
1.	1
ii.	<button className="delete-button-heading" onClick={handleDeleteTodo}>Delete Heading</button>
Copied!
Click here for the solution code of TodoList.jsx
1.	import React, { useState } from 'react';
2.	import './TodoList.css';
3.	
4.	const TodoList = () => {
5.	    const [todos, setTodos] = useState([]);
6.	    const [headingInput, setHeadingInput] = useState('');
7.	    const [listInputs, setListInputs] = useState({});
8.	
9.	    const handleAddTodo = () => {
10.	        if (headingInput.trim() !== '') {
11.	            setTodos([...todos, { heading: headingInput, lists: [] }]);
12.	            setHeadingInput('');
13.	        }
14.	    };
15.	
16.	     const handleDeleteTodo = (index) => {
17.	        const newTodos = [...todos];
18.	        newTodos.splice(index, 1);
19.	        setTodos(newTodos);
20.	      };
21.	
22.	    const handleAddList = (index) => {
23.	        if (listInputs[index] && listInputs[index].trim() !== '') {
24.	            const newTodos = [...todos];
25.	            newTodos[index].lists.push(listInputs[index]);
26.	            setTodos(newTodos);
27.	            setListInputs({ ...listInputs, [index]: '' });
28.	        }
29.	    };
30.	
31.	    const handleListInputChange = (index, value) => {
32.	        setListInputs({ ...listInputs, [index]: value });
33.	    };
34.	
35.	    return (
36.	        <>
37.	            <div className="todo-container">
38.	                <h1 className="title">My Todo List</h1>
39.	                <div className="input-container">
40.	                    <input
41.	                        type="text"
42.	                        className="heading-input"
43.	                        placeholder="Enter heading"
44.	                        value={headingInput}
45.	                        onChange={(e) => setHeadingInput(e.target.value)}
46.	                    />
47.	                    <button className="add-list-button" onClick={handleAddTodo}>Add Heading</button>
48.	                </div>
49.	            </div>
50.	            <div className="todo_main">
51.	                {todos.map((todo, index) => (
52.	                    <div key={index} className="todo-card">
53.	                        <div className="heading_todo">
54.	                            <h3>{todo.heading}</h3>
55.	                            <button className="delete-button-heading" onClick={() => handleDeleteTodo(index)}>Delete Heading</button>
56.	                        </div>
57.	                        <ul>
58.	                            {todo.lists.map((list, listIndex) => (
59.	                                <li key={listIndex} className='todo_inside_list'>
60.	                                    <p>{list}</p>
61.	                                </li>
62.	                            ))}
63.	                        </ul>
64.	                        <div className='add_list'>
65.	                            <input
66.	                                type="text"
67.	                                className="list-input"
68.	                                placeholder="Add List"
69.	                                value={listInputs[index] || ''}
70.	                                onChange={(e) => handleListInputChange(index, e.target.value)}
71.	                            />
72.	                            <button className="add-list-button" onClick={() => handleAddList(index)}>Add List</button>
73.	                        </div>
74.	                    </div>
75.	                ))}
76.	            </div>
77.	        </>
78.	    );
79.	};
80.	
81.	export default TodoList;
Copied!
PreviousNext



