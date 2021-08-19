# what is node and how it works 

Node js 
1. javascript runtime built on chrome V8 javascript engine 
2. is single threaded but can handle more concurrent client requests as it follows single threaded with event loop model . 
3. event loop is the secret behind javascript asynchronous programming . 
4. when an async function is called , it is sent to a browser API 
These are APIs built into the browser . Based on the command received from the call stack , the API starts its own single-threaded operation . 
5. When a setTimeout operation is processed , the operation is sent into the event queue . Hence we have cyclic system for running async operations in JavaScript . The language itself is single threaded , but the browser APIs acts as separate threads . 
6. The event loop facilates this process ; it constantly checks whether or not the call stack is empty . If it is empty , new functions are added from the event queue . If it is not , then the current function call is processed . 
    
Single Thread 
A single thread language is one with a single call stack and a single memory heap . It means that it runs only one thing at a time . 
1. A stack is a continuous region of memory, allocating local context for each executed function
2. A heap is a much larger region, storing everything allocated dynamically.
3. A call stack is a data structure which basically records where we are in the program.
![](https://thecodest.co/images/uploaded/2020/03/asynchronous-and-single-threaded-javascript-meet-the-event-loop/callback-queue.gif)

Event Loop 
- Event loop is a part of the JS engine . This process constantly checks if the call stack is empty end , and if it is , monitors whether there is an event in the callback queue waiting to be invoked 

Synchronous & Asynchronous 
- In synchronous programming , tasks are executed one after another . Each tasks waits for any previous task to be completed and is executed only then . 
- In asynchronous programming , when one task is executed , you can switch to a different task without waiting for the previous one to be completed . 
    
Synchronous and asynchronous in a single and multi threaded environment 
- Synchronous with a single thread: Tasks are executed one after another. Each task waits for its previous task to get executed.
-Synchronous with multiple threads: Tasks are executed in different threads but wait for any other executing tasks on any other thread.
- Asynchronous with a single thread: Tasks start being executed without waiting for a different task to finish. At a given time, only a single task can be executed.
- Asynchronous with multiple threads: Tasks get executed in different threads without waiting for other tasks to be completed and finish their executions independently.
