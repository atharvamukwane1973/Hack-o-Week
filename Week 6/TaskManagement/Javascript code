let tasks = JSON.parse(localStorage.getItem("tasks")) || {};

let dateInput = document.getElementById("date");
let today = new Date().toISOString().split("T")[0];

function isPast(date){
return date < today;
}

function addTask(){

let date = dateInput.value;
let text = document.getElementById("taskInput").value;

if(date === "" || text === ""){
alert("Select date and enter task");
return;
}

if(isPast(date)){
alert("You cannot add tasks to past dates");
return;
}

if(!tasks[date]){
tasks[date] = [];
}

tasks[date].push({
text:text,
completed:false
});

localStorage.setItem("tasks", JSON.stringify(tasks));

document.getElementById("taskInput").value="";

showTasks();
}

function showTasks(){

let date = dateInput.value;
let list = document.getElementById("taskList");

list.innerHTML="";

let completed=0;

if(tasks[date]){

tasks[date].forEach((task,index)=>{

let li=document.createElement("li");

let span=document.createElement("span");
span.textContent=task.text;

if(task.completed){
span.classList.add("completed");
completed++;
}

span.onclick=()=>{
if(!isPast(date)){
toggleTask(date,index);
}
}

let actions=document.createElement("div");
actions.className="actions";

if(!isPast(date)){

let edit=document.createElement("span");
edit.textContent="✏";
edit.className="edit";
edit.onclick=()=>editTask(date,index);

let del=document.createElement("span");
del.textContent="❌";
del.className="delete";
del.onclick=()=>deleteTask(date,index);

actions.appendChild(edit);
actions.appendChild(del);

}

li.appendChild(span);
li.appendChild(actions);

list.appendChild(li);

});

}

updateProgress(completed, tasks[date] ? tasks[date].length : 0);

}

function toggleTask(date,index){

tasks[date][index].completed=!tasks[date][index].completed;

localStorage.setItem("tasks", JSON.stringify(tasks));

showTasks();

}

function deleteTask(date,index){

tasks[date].splice(index,1);

localStorage.setItem("tasks", JSON.stringify(tasks));

showTasks();

}

function editTask(date,index){

let newTask=prompt("Edit task",tasks[date][index].text);

if(newTask){
tasks[date][index].text=newTask;
}

localStorage.setItem("tasks", JSON.stringify(tasks));

showTasks();

}

function updateProgress(done,total){

document.getElementById("progressText").textContent=
done+" / "+total+" Completed";

}
