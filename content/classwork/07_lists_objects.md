# 07. სიები და ობიექტები
სწავლას ვაგრძელებთ ხანის აკადემიაზე. ხანის აკადემიის ინსტრუქცია და მეცადინეობის პრინციპი მე-5 სემინარში წერია. **ამ სემინარის გასაგებად აუცილებელია წინა ორი კვირის სემინარის გავლა.**

გავაკეთეთ ყველა სავარჯიშო ქვემოთ მოცემულ თავებში:

- [მასივები][1]
- [ობიექტები][2]


### სავარჯიშოების გავრცობა
ქვემოთ არის რამდენიმე სავარჯიშოს ალტერნატიული პირობა/ამოხსნა. სხვა სავარჯიშოები მაინც გასაკეთებელია, მაგრამ ამათზე მნიშვნელოვანია ეს დამატებითი ნაწილებიც გაარჩიოთ.

## მასივები
### საყვარელი ცხოველები
while-ის მაგივრად for ცილკით ასე დაიწერებოდა:
```js
var favoriteAnimals = ["parrots", "cats", "dogs", "dolphin"];

fill(0, 0, 0);
for (var i=0; i<favoriteAnimals.length; i++) {
    text(favoriteAnimals[i], 200, 200+20*i);
}
```


### თანავარსკვლავედების შემქმნელი
მოდი ერთი გრძელი image() ხაზის მაგივრად, მისი არგუმენტები (x, y, star), ცალკე ცვლადებად გავიტანოთ. ასე კოდი უფრო წაკითხვადი ხდება. 
```js
var xPositions = [100, 200, 197];
var yPositions = [200, 30, 150];

var drawStars = function() {
    background(9, 5, 59);
    imageMode(CENTER);
    var star = getImage("space/star");
    for (var i = 0; i < yPositions.length; i++) {
        var x = xPositions[i];
        var y = yPositions[i];
        text(i, x, y-20);
		image(star, x, y, 30, 30);
    }
};
```


ახლა წინა კვირას რომ random() ფუნქცია შეგვხვდა, ეგ გამოვიყენოთ და ვარსკვლავები შემთხვევით შერჩეულ x/y კოორდინატებზე დაიხატება.

```js
var drawManyStars = function() {
    background(9, 5, 59);
    imageMode(CENTER);
    var star = getImage("space/star");
    for (var i = 0; i < 330; i++) {
        var x = random(0, 358);
        var y = random(0, 364);
		text(i, x, y-20);
        image(star, x, y, 20, 20);
    }
};

drawManyStars();

```

## ობიექტები
### ფილმის მიმოხილვა
დასაწყისისთვის, movies ცვლადში კიდევ 1-2 წიგნი ჩაამატე. მოდი, for ციკლში ჩასმამდე, არსებული კოდი ფუნქციად გადავაკეთოთ. დააკვირდი, რომელ ხაზებში გამოიყენება არგუმენტები

```js
function displayMovie(movie, yStart) {
    fill(84, 140, 209);
    textAlign(CENTER, CENTER);
    textSize(20);
    
    text(movie.title, 200, yStart);
    
    fill(0, 0, 0);
    textSize(13);
    
    text(movie.review, 151, yStart + 30);
}
```

ამის შემდეგ უფრო მარტივი იქნება ციკლში ჩასმა. თუ `88+98*i` არ გესმის რატომ წერია, დაუბრუნდი წინა კვირის სავარჯიშოებს.
```js
for (var i=0; i < movies.length; i++) {
    displayMovie(movies[i], 50 + 100*i);
}
```

[1]:	https://ka.khanacademy.org/computing/computer-programming/programming/arrays/pt/intro-to-arrays
[2]:	https://ka.khanacademy.org/computing/computer-programming/programming/objects/pt/intro-to-objects