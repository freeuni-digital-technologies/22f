# 02. კარელი - სავარჯიშოები

**ვიდეოები ნახეთ ყველამ და ვიდეოს სავარჯიშოებიც (example რასაც აწერია) გააკეთეთ დამოუკიდებლად**. ამოცანების გარდა გირჩევთ ივარჯიშოთ 
[keyboard shortcut][1]-ების გამოყენებაშიც.

#### ამ გვერდზე მოცემულია
- codehs მეორე კვირის სავარჯიშოების პასუხები
- ამოხსნის ალტერნატიული ვარიანტები. მარტივად რომ შეადარო ერთმანეთს, დანომრილია.
- პირობების მოდიფიკაციები 

??? Note "codehs ინსტრუქცია"
```
{%
   include-markdown "../classwork/01_karel_setup.md"
   start="### codehs"
   heading_offset="2"
   end="მთავარი თემები"
%}
```

#### მითითებები მეცადინეობისთვის:
- აუცილებლად მიყევი სავარჯიშოებს ამ გვერდთან ერთად.
- ყველა სავარჯიშოს ამ კვირასვე ვერ გააკეთებ, მაგრამ დავალებისთვის არ არის აუცილებელი
- გახსენი codehs-ზე და წაიკითხე ხოლმე აქედან შენიშვნები, რომ ყველა მნიშვნელოვანი დეტალი გაიარო. 
- კოდი არ გადააკოპირო. პირველად შეეცადე ნახვამდე შენით დაწერო, თუ არ გამოგივიდა, შეხედე, წაიკითხე და პასუხის ყურების გარეშე დაწერე
- გაითვალისწინე, რომ კოდში ფუნქცია start()-ს არ ვიყენებ და შენ უნდა გამოიძახო მთავარი ფუნქცია (პირველი რომელიც წერია ხოლმე) სტარტში

## 2.1.4 Pancakes
კარელმა უნდა დადოს 3 ბურთი ყოველ მე-3 უჯრაზე

### "მარტივი" კოდი

```js
function pancakes1() {
    move();
    putBall();
    putBall();
    putBall();
    move();
    move();
    putBall();
    putBall();
    putBall();
    move();
    move();
    putBall();
    putBall();
    putBall();
    move();
    move();
}
```

რა მოხდება, თუ გვთხოვენ სამის მაგივრად ოთხი ბურთი დავდოთ თითოეულ უჯრაზე?


### ფუნქციის გამოყენება

```js
function pancakesWithFunction() {
    makePancake();
    makePancake();
    makePancake();
}

function makePancake() {
    move();
    putBall();
    putBall();
    putBall();
    move();
}
```

### დეკომპოზიცია

```js
function pancakesDecomposed() {
    makePancake();
    makePancake();
    makePancake();
}

function makePancake() {
    move();
    putBalls();
    move();
}

function putBalls() {
    putBall();
    putBall();
    putBall();
}
```



## 2.1.5: Backflip
```js
function start() {
    moveAndBackFlip();
    moveAndBackFlip();
}

function moveAndBackFlip() {
    move();
    move();
    backFlip();
}
function backFlip() {
    turnLeft();
    turnLeft();
    turnLeft();
    turnLeft();
}
```


## 3.3.6: Dizzy Karel
### მარტივი ამოხსნა
თუ დავაკვირდებით, რომ 8-ჯერ დატრიალება 32-ჯერ მარცხნივ შეტრიალებას ნიშნავს, ამოცანა ძალიან მარტივად ამოხსნება.


```js

function dizzySimple() {
    for (var i = 0; i < 32; i++) {
        turnLeft();
    }
    move();
}
```

### nesting
ყოველთვის ამის საშუალებას არ მოგვცემს პირობა, ამიტომ 

```js
function dizzyNested() {
    for (var i = 0; i < 8; i++) {
        for (var i = 0; i < 4; i++) {
            turnLeft();
        }
    }
}
```

### დეკომპოზიცია
"მუშა" კოდის დაწერის შემდეგ გავაკეთოთ კიდევ ერთი გადახედვა და დავფიქრდეთ, ხომ არ შეგვიძლია კოდის ხარისხი გავაუმჯობესოთ?


```js
function dizzyDecomposed() {
    for (var i = 0; i < 8; i++) {
        backFlip();
    }
}

function backFlip() {
    for (var i = 0; i < 4; i++) {
        turnLeft();
    }
}
```

## 4.1.5: Is There a Ball?
ეს ამოცანა პატარაა, მაგრამ მაინც top down დიზაინით გავაკეთოთ. ამისთვის უბრალოდ პირობა "გადავწეროთ კოდში".


## 5.1.3: Move to Wall
## 5.1.5: Lay Row of Tennis Balls
 Off by one bug

```js
function fillLineBuggy(){
    while(frontIsClear()) {
        putBall();
        move();
    }
}
```

### ორნაირი ამოხსნა

```js
function fillLine1() {
    putBall();
    while(noBallsPresent()) {
        move();
        putBall();
    }
}

function fillLine2() {
    while(noBallsPresent()) {
        putBall();
        move();
    }
    putBall();
}
```

### ალტერნატიული ამოხსნა

```js
function fillLine3() {
	while(noBallsPresent()) {
        putBall();
        if (frontIsClear()) {
            move();
        }
    }
}
```

[1]:	https://help.codehs.com/en/articles/4502500-for-students-keyboard-shortcuts