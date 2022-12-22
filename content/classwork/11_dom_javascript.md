# 11. DOM javascript
ამ სემინარზე განვიხილეთ

- Document Object Model
- DOM ელემენტების მოდიფიკაცია
- DOM ელემენტების შექმნა
- რამდენიმე ახალი html თეგი (button, input)

ხანის აკადემიაზე შესაბამისი მასალა - [HTML/JS: ინტერაქტიული ვებგვერდების გაკეთება][1]:

- JS და DOM
- DOM წვდომის მეთოდები
- DOM მოდიფიცირება


ქვემოთ მოცემული კოდი უბრალოდ წასაკითხად არ არის, ვერ გაიგებ თუ თვითონ არ დაწერე და ნახე რას აკეთებს. ამისთვის შექმენი ახალი html/js ფაილები და ჩაწერე კოდი იქ. შემდეგ გახსენი ბრაუზერში. თუ copy/paste-ს გამოიყენებ, მნიშვნელოვან შეცდომებს ვერ დაუშვებ და დავალების გაკეთება ძალიან გაგიჭირდება.


## მარტივი მაგალითები
### 1. ღილაკზე დაჭერით ტექსტის გამოჩენა
```html
<div id="message"></div>
<button onclick="sayHello()">say hi</button>

<script>
function sayHello() {
	let messageDiv = document.getElementById('message')
	messageDiv.innerText = "hello"
}
</script>

```

### 2. counter
```html
<div id="counter"></div>
<button onclick="increaseCounter()">increase counter</button>
<script>
let i = 0;	
function increaseCounter() {
	i++
	let counterDiv = document.getElementById('counter')
	counterDiv.innerText = i
}
</script>
```

### 3. user input
```html
<input id="name">
<button onclick="greet()">greet</button>
<div id="greeting"></div>
<script>
function greet() {
	let name = document.getElementById('name').value
	let greetingDiv = document.getElementById('greeting')
	greetingDiv.innerText = "hello, " + name
}
</script>
```


## todo list აპლიკაცია
აქ სავარჯიშო რამდენიმე ეტაპადაა მოცემული. ასეთ დროს თითოეული ეტაპი უნდა დაწერო და ნახო ცალ-ცალკე
### საწყისი კოდი
#### index.html
html კოდი სავარჯიშოს განმავლობაში არ შეიცვლება.
```html
<div>
	<input id="task-input">	
	<button id="add-task" onclick="addTask()">add task</button>
	<div id="tasks"></div>
</div>
<script src="index.js"></script>
```

#### index.js
ქვემოთ ყველა სხვა ნაბიჯში იგულისხმე, რომ იცვლება index.js ფაილი.

```js
function addTask() {
	console.log('button clicked')
}
```

გახსენი index.html ბრაუზერში, შემდეგ გახსენი კონსოლი და დააჭირე ღილაკს. კონსოლში უნდა დაიწეროს "button clicked"

### მარტივი ფუნქციონალი
ახალი ელემენტის შექმნამდე, უბრალოდ tasks div-ში ჩავწეროთ ტექსტი (greet-ის მსგავსად). შეცვალე ფუნქცია `addTask()`. ამიერიდან, თუ კოდში წერია არსებული ფუნქციის სახელი, ის ფუნქცია უნდა შეცვალო. თუ ახალი ფუნქციის სახელია, უნდა დაამატო.
```js
function addTask() {
	let taskText = document.getElementById('task-input').value
	let tasksElem = document.getElementById('tasks')
	tasksElem.innerText = taskText
}
```

### ახალი ელემენტის შექმნა
დააკვირდი, რომ პირველი ორი ხაზი იგივე რჩება
```js
function addTask() {
	let taskText = document.getElementById('task-input').value
	let tasksElem = document.getElementById('tasks')
	let taskDiv = document.createElement('div')
	taskDiv.innerHTML = taskText
	taskDiv.appendChild(taskTextDiv)
}
```

### რეფაქტორინგი
შემდეგი ნაბიჯისთვის გვინდა თითოეულ თასქს ქონდეს ღილაკი, რომლითაც მას შესრულებულად მოვნიშნავთ ხოლმე. `addTask()` ფუნქცია უკვე საკმარისი ზომისაა და კიდევ მეტი კოდის ჩამატებით აირევა. ამიტომ, წინასწარვე მოვამზადოთ ახალი ფუნქცია.

**მნიშვნელოვანია**, რომ თუ ახალი ფუნქციისას რეფაქტორინგის აუცილებლობას მიხვდი, ჯერ არსებულ ფუნქციონალზე გააკეთო რეფაქტორინგი.

```js
function createTaskElem(taskText) {
	let taskDiv = document.createElement('div')
	taskDiv.innerHTML = taskText
	return taskDiv
}
```

გახსენი კონსოლი და გამოიძახე `createTaskElem()` ფუნქცია. არგუმენტად რამე სტრინგი გადააწოდე, მაგალითად `createTaskElem("mytask")`. შემდეგ კი მთავარ ფუნქციაშიც გამოიძახე

```js
function addTask() {
	let taskText = document.getElementById('task-input').value
	let tasksElem = document.getElementById('tasks')
	let taskDiv = createTaskElem(taskText)
	taskDiv.appendChild(taskTextDiv)
}
```

### ღილაკის დამატება
```js
function createTaskElem(taskText) {
	let taskDiv = document.createElement('div')

	let doneTaskButton = createTaskButton()
	taskDiv.appendChild(doneTaskButton)
	
	let taskTextSpan = createTastText(taskText)
	taskDiv.appendChild(taskTextSpan)
	
	return taskDiv
}

function createTaskButton() {
	let button = document.createElement('button')
	button.innerText = '☑️'
	return button
}

function createTaskText(taskText) {
	let span = document.createElement('span')
	span.innerText = taskText
	return span
}
```

შეგიძლია სტილის თეგი ისე შეცვალო, რომ ღილაკი და ტექსტი ერთმანეთის გვერდიგვერდ გამოჩნდნენ?

!!! tip "ბონუს ამოცანა"
```
შემდეგი კვირისთვის თუ თასქის შესრულებულად მონიშვნის ღილაკს აამუშავებ, მოგვწერე მეილზე და ბონუს ქულას დაგიწერთ 
```

[1]:	https://ka.khanacademy.org/computing/computer-programming/html-css-js