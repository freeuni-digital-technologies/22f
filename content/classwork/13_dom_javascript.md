# 13. DOM javascript
ამ გვერდზე მოცემულია 12-13 კვირებში განხილული მასალა

ხანის აკადემიაზე შესაბამისი გაკვეთილები (თუ სემინარი გააცდინე ან რამე ფუნქცია გაუგებარია, ნახე ვიდეოები) - [HTML/JS: ინტერაქტიული ვებგვერდების გაკეთება][1]:

- JS და DOM
- DOM წვდომის მეთოდები
- DOM მოდიფიცირება

ქვემოთ მოცემული კოდი უბრალოდ წასაკითხად არ არის, ვერ გაიგებ თუ თვითონ არ დაწერე და ნახე რას აკეთებს. ამისთვის შექმენი ახალი html/js ფაილები და ჩაწერე კოდი იქ. შემდეგ გახსენი ბრაუზერში. თუ copy/paste-ს გამოიყენებ, მნიშვნელოვან შეცდომებს ვერ დაუშვებ და დავალების გაკეთება ძალიან გაგიჭირდება.


## მარტივი მაგალითები
### 1. ღილაკზე დაჭერით ტექსტის გამოჩენა
```html
<div id="message"></div>
<button id="say-hello-button">say hi</button>

<script>
function sayHello() {
	let messageDiv = document.getElementById('message')
	messageDiv.innerText = "hello"
}
document.getElementById("say-hello-button").addEventListener('click', sayHello)
</script>

```

დააკვირდი, რომ `addEventListener`-ში `sayHello` წერია და არა `sayHello()` (ფრჩხილების გარეშეა). ეს ძალიან მნიშვნელოვანი განსხვავებაა - ღილაკზე ფუნქცია რომ მივაბათ, ფუნქციის **სახელი** უნდა გადავაწოდოთ. გვერდის ჩატვირთვისას, როდესაც ღილაკს ფუნქციას ვუკავშირებთ, გამოძახება ხომ არ გვჭირდება - უბრალოდ უნდა **მივუთითოთ** ფუნქციაზე.

### 2. counter
```html
<div id="counter"></div>
<button id="increase-counter-button">increase counter</button>
<script>
let i = 0;	
function increaseCounter() {
	i++
	let counterDiv = document.getElementById('counter')
	counterDiv.innerText = i
}
document.getElementById("increase-counter-button").addEventListener('click', increaseCounter)
</script>
```

### 3. user input
```html
<input id="name">
<button id="greet">greet</button>
<div id="greeting"></div>
<script>
function greet() {
	let name = document.getElementById('name').value
	let greetingDiv = document.getElementById('greeting')
	greetingDiv.innerText = "hello, " + name
}
document.getElementById("greet-button").addEventListener('click', greet)
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
	<button id="add-task">add task</button>
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
document.getElementById("add-task").addEventListener("click", addTask)
```

[1]:	https://ka.khanacademy.org/computing/computer-programming/html-css-js