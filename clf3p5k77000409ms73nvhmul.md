---
title: "ToDo List Smart Contract"
datePublished: Sat Mar 11 2023 08:20:29 GMT+0000 (Coordinated Universal Time)
cuid: clf3p5k77000409ms73nvhmul
slug: todo-list-smart-contract
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678522312745/326e6aa9-9bcd-4e01-9c20-cff600b4b26a.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678522812237/de7b3e89-b208-4815-9a4c-ea20838ef331.png
tags: projects, blockchain, ethereum, web3, smart-contracts

---

## ToDo List Smart Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract TaskContract {
    constructor() {
        
    }

    struct Task {
        uint id;
        string taskTitle;
        string taskText;
        bool isDeleted;
    }

    Task[] private tasks;
    
    mapping (uint => address) taskToOwner;
    
    event AddTask(address recepient,uint taskId);

    event DeleteTask(uint taskId,bool isDeleted);

    function addTask(string memory taskText,string memory taskTitle, bool isDeleted) external {
        uint taskId = tasks.length;
        tasks.push(Task(taskId,taskTitle, taskText, isDeleted));
        taskToOwner[taskId] = msg.sender;
        emit AddTask(msg.sender,taskId);
    }


    function deleteTask(uint taskId) external {
        require(taskToOwner[taskId] == msg.sender, "You are not the owner of this task");
        tasks[taskId].isDeleted = true;
        emit DeleteTask(taskId,tasks[taskId].isDeleted);
    }

    function getMyTask()public view returns(Task[] memory){
        Task[] memory myTasks = new Task[](tasks.length);
        uint counter = 0;
        for(uint i = 0; i < tasks.length; i++){
            if(taskToOwner[i] == msg.sender && tasks[i].isDeleted == false){
                myTasks[counter] = tasks[i];
                counter++;
            }
        }
        Task[] memory result = new Task[](counter);
        for(uint i = 0; i < counter; i++){
            result[i] = myTasks[i];
        }
        return result;
    }

}
```

## Explanation and Breakdown

```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract TaskContract {
    constructor() {
        
    }
struct Task {
        uint id;
        string taskTitle;
        string taskText;
        bool isDeleted;
    }

    Task[] private tasks;
    
    mapping (uint => address) taskToOwner;
    
    event AddTask(address recepient,uint taskId);

    event DeleteTask(uint taskId,bool isDeleted);
```

* The code defines a struct called Task with four fields: an ID (uint), a task title (string), a task text (string), and a Boolean flag indicating whether the task has been deleted (bool).
    
* The code declares a private Task array called tasks to store all the tasks created by the contract.
    
* The code defines a mapping called taskToOwner, which maps a task ID (uint) to the address of the user who created the task.
    
* The code includes two events:
    
    * AddTask: emitted when a new task is added to the tasks array. The event includes the address of the user who added the task and the ID of the new task.
        
    * DeleteTask: emitted when a task is marked as deleted in the tasks array. The event includes the ID of the deleted task and a flag indicating that it has been deleted.
        
* The code uses these constructs to define the data model for a task management system, where tasks are represented by the Task struct, stored in the tasks array, and associated with their creators via the taskToOwner mapping. The events allow for tracking and auditing of task creation and deletion.
    

```solidity
 function addTask(string memory taskText,string memory taskTitle, bool isDeleted) external {
        uint taskId = tasks.length;
        tasks.push(Task(taskId,taskTitle, taskText, isDeleted));
        taskToOwner[taskId] = msg.sender;
        emit AddTask(msg.sender,taskId);
    }


    function deleteTask(uint taskId) external {
        require(taskToOwner[taskId] == msg.sender, "You are not the owner of this task");
        tasks[taskId].isDeleted = true;
        emit DeleteTask(taskId,tasks[taskId].isDeleted);
    }
```

* The `addTask` function is a public function that takes three arguments: a string for the task text, a string for the task title, and a boolean indicating whether the task is marked as deleted. It is used to add new tasks to the `tasks` array and associate the new task with the caller's address via the `taskToOwner` mapping.
    
* Within the function, the ID for the new task is set to the length of the `tasks` array. A new task with the given text, title, and deletion flag is created using the `Task` struct constructor and added to the `tasks` array.
    
* The caller's address is then associated with the new task ID in the `taskToOwner` mapping.
    
* Finally, an `AddTask` event is emitted with the caller's address and the ID of the new task.
    
* The `deleteTask` function is a public function that takes one argument: the ID of the task to be deleted. It is used to mark a task as deleted in the `tasks` array.
    
* Within the function, the caller's address is checked against the address associated with the given task ID in the `taskToOwner` mapping to ensure that the caller is the owner of the task.
    
* If the caller is the owner of the task, the `isDeleted` flag for the task is set to `true` in the `tasks` array.
    
* Finally, a `DeleteTask` event is emitted with the ID of the deleted task and a flag indicating that it has been marked as deleted.
    

```solidity
function getMyTask()public view returns(Task[] memory){
        Task[] memory myTasks = new Task[](tasks.length);
        uint counter = 0;
        for(uint i = 0; i < tasks.length; i++){
            if(taskToOwner[i] == msg.sender && tasks[i].isDeleted == false){
                myTasks[counter] = tasks[i];
                counter++;
            }
        }
        Task[] memory result = new Task[](counter);
        for(uint i = 0; i < counter; i++){
            result[i] = myTasks[i];
        }
        return result;
    }
```

* The `getMyTask` function is a public function that returns an array of `Task` struct objects for the caller. It is used to retrieve all non-deleted tasks associated with the caller's address in the `tasks` array.
    
* Within the function, a new `Task` array called `myTasks` is created with the same length as the `tasks` array. A counter variable is also initialized to 0.
    
* A for loop is used to iterate over all tasks in the `tasks` array. If a task is associated with the caller's address in the `taskToOwner` mapping and is not marked as deleted, it is added to the `myTasks` array at the current index indicated by the `counter` variable, and the `counter` variable is incremented.
    
* After the first for loop, a new `Task` array called `result` is created with a length equal to the `counter` variable.
    
* A second for loop is used to iterate over the `myTasks` array and populate the `result` array with the non-null `Task` objects.
    
* Finally, the `result` array is returned as the result of the `getMyTask` function.
    

## Github Repo

[Smart Contract Repo basics to advanced](https://github.com/moayaan1911/smart-contracts)