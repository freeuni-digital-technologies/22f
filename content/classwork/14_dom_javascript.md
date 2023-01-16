# 14. DOM Javascript -  todo list app

ვაგრძელებთ წინა კვირის სემინარზე დაწყებული კოდის გავრცობას. კიდევ ერთხელ გავიმეორებ, რომ თუ შენით არ შექმნი ფაილებს და დაწერ კოდს, საკმარისად ვერ ივარჯიშებ რომ კითხვებს პასუხი გასცე. მხოლოდ სემინარზე ყურება და შემდეგ "თვალის გადავლება" არ გეყოფა გამოცდისთვის საჭირო გაგების ასათვისებლად.

### html body (წინა კვირიდან)
```html
<div>	
	<input id="task-input">	
	<button id="add-task">add task</button>
	<div id="tasks"></div>
</div>
<script src="index.js"></script>
```


### თასქის დამატება
დააკვირდი, რომ პირველი ორი ხაზი იგივე რჩება
```js
function addTask() {
	// შეყვანილი ტექსტის წაკითხვა
	let taskText = document.getElementById('task-input').value
	
	// ელემენტის შექმნა
	let taskElement = document.createElement('div')
	taskElement = taskText

	// ელემენტის დამატება tasks დივში 
	let tasksDiv = document.getElementById('tasks')
	tasksDiv.appendChild(taskElement)
}
```

### რეფაქტორინგი
შემდეგი ნაბიჯისთვის გვინდა თითოეულ თასქს ქონდეს ღილაკი, რომლითაც მას შესრულებულად მოვნიშნავთ ხოლმე. `addTask()` ფუნქცია უკვე საკმარისი ზომისაა და კიდევ მეტი კოდის ჩამატებით აირევა. ამიტომ, წინასწარვე მოვამზადოთ ახალი ფუნქცია.

**მნიშვნელოვანია**, რომ თუ ახალი ფუნქციისას რეფაქტორინგის აუცილებლობას მიხვდი, ჯერ არსებულ ფუნქციონალზე გააკეთო რეფაქტორინგი.

#### ახალი ელემენტის შექმნა
```js
function createTaskElement(taskText) {
    let myDiv = document.createElement('div')
    myDiv.innerText = taskText
    myDiv.className = 'task-div'
    return myDiv
}
```

გახსენი კონსოლი და გამოიძახე `createTaskElement()` ფუნქცია. არგუმენტად რამე სტრინგი გადააწოდე, მაგალითად `createTaskElement("mytask")`. შემდეგ კი მთავარ ფუნქციაშიც გამოიძახე

#### ელემენტის დამატება
შევქმნათ ფუნქცია, რომელსაც გადავაწვდით რამე ელემენტს, და მას დაამატებს თასქების დივში
```js
function addTaskElement(element) {
    document.getElementById('tasks').appendChild(element)
}
```

გახსენი კონსოლი და გამოიძახე `createTaskElement()` ფუნქცია, ოღონდ ამჯერად მისი დაბრუნებული მნიშვნელობა შეინახე, და შემდეგ თასქის დამატების ფუნქციას გადააწოდე.

```js
> let taskElement = createTaskElement("my task")
> taskElement // დარწმუნდი, რომ ცვლადში dom ელემენტია შენახული
> addTaskElement(taskElement) // ახლა კი 
```

ეს ხაზები შემდეგის ეკვივალენტურია:
```js
addTaskElement(createTaskElement("my task"))
```

#### მთავარი ფუნქციის განახლება
ახლა დროა ორი ახალი ფუნქცია სწორად გამოვიყენოთ
```js
function addTask() {
    let taskText = document.getElementById('task-input').value
    let taskElement = createTaskElement(taskText)
    addTaskElement(taskElement)
}
```

