# 15. ციფრული უსაფრთხოება


## რესურსებზე წვდომა
შენი აზრით, რა წვდომა აქვთ შენს ინფორმაციაზე:
- საიტებს
- გადმოწერილ აპლიკაციებს
- wifi-ს სხვა მომხმარებლებს
- ქლაუდ აპლიკაციის მფლობელ კომპანიას 
- ორგანიზაციის ექაუნთებს
- ელექტრონული მოწყობილობის გამომშვებ კომპანიას
- ოპერატიული სისტემის გამომშვებ კომპანიას

### მოწყობილობა
ვის შეუძლია წაიკითხოს/დააკოპიროს შენი ფაილები?
- ოპერატიული სისტემის კომპანიას (Android/Microsoft)
- ლეპტოპ ოპერატიული სისტემის (Windows/MacOS/Linux) შემთხვევაში, ყველა პროგრამას, რომელსაც გადმოწერ
- მობილური ოპერატიული სისტემის შემთხვევაში (android/iOS/lineageOS) აპლიკაციებს გრანულარულად
<!-- n -->
გრანულარული წვდომა ნიშნავს, რომ ყველა აპლიკაციამ **სათითაოდ** უნდა მოითხოვოს სხვადასხვა რესურსების წაკითხვაზე (სურათები, ფაილები, კალენდარი, და ა.შ.) უფლება, თუმცა მასზე ნებართვის მოპოვების შემდეგ, შეუძლია სურვილისამებრ გამოიყენოს. წვდომის მოთხოვნის ვალიდურობასა და მონაცემთა დათქმული მიზნით გამოყენებას Apple და Google უზრუნველყოფენ - ამიტომაა საჭირო App/Play Store-ზე აპლიკაციის გამოქვეყნებისას მკაცრი და ზოგჯერ გრძელვადიანი Review.

### cloud პროდუქტებზე
ვის აქვს წვდომა ინფორმაციაზე, რომელსაც ინახავს გუგლი? ეფლი?

<!-- n -->
აპლიკაციების დაცული პაროლი მხოლოდ სხვა ადამიანებისგან იცავს, მაგრამ შენი ფაილები ისევე ინახება გუგლის კომპიუტერზე (სერვერზე), როგორც შენსაზე. გუგლის თითქმის ყველა პროგრამას შეუძლია თავისუფლად წაიკითხოს და გამოიყენოს (კლავიატურის გამოყენებაც კი)
ეფლის შემთხვევაში ეს მონაცემები ასევე სერვერზე ინახება, თუმცა გაგზავნამდე შენი პაროლით იშიფრება, რომელზე წვდომაც ეფლს არ აქვს. ამ საკითხის უფრო სიღრმისეულად განხილვა სამწუხაროდ ვერ მოვასწარით, თუმცა მეტი ინფორმაციისთვის, შეგიძლია წაიკითხო Client Side Encryption-ის შესახებ

### ქსელი
### wifi
ყველას, ვინც ქსელშია (ვინც პაროლი იცის)

<!-- ნ -->
wifi ეფექტურად არის შიდა ქსელი და ნებისმიერს ამ ქსელში შეუძლია ნახოს ყველა შენი კომუნიკაცია. ოთახში ხმამაღლა ლაპარაკს გავს.

### ინტერნეტში გზავნილზე
- გამგზავნის ISP-ს
- მიმღების ISP-ს
- შუალედურ ISP-ს
- inteceptor-ს (სრულიად შესაძლებელია მესამე პირის მიერ მოსასმენი მოწყობილობის დაყენება შნურზე)

<!-- ნ -->
როგორ მოვახერხოთ უსაფრთხოების და პირადი ინფორმაციის შენახვა ამ პირობებში? როგორ აკეთებდით ამას სკოლაში?


## დაშიფვრა
<!-- n -->
ყველამ იცის, რომ მთელი პლანეტის ფუნქციონირება, ინფორმაციის კონფიდენციალურობა და ფინანსური ტრანზაქციების უსაფრთხოება დაშიფვრის ალგორითმების წყალობითაა შესაძლებელი. დაშიფვრის მუშაობის პრინციპისა და ყველასთვის მნიშვნელოვანი დეტალების გასაგებად კომპიუტერული მეცნიერების სწავლა არაა აუცილებელი, შეგვიძლია ყოფითი მაგალითით განვიხილოთ. 

წარმოვიდგინოთ, რომ გვყავს ორი ადამიანი, რომელსაც წერილის (ინტერნეტ პაკეტი) გაგზავნა უნდა ფოსტის (ინტერნეტი) საშუალებით. წერილის შინაარსი კრიტიკულად პირადულია, და გვინდა ყველაფერი მოვიმოქმედოთ იმისთვის, რომ გზაში სხვა პირებმა იგი გახსნის შემთხვევაშიც ვერ წაიკითხოს.

### მარტივი
![][image-1]
<!-- n -->
წარმოიდგინე კოდი, რომელზეც წინასწარ შეთანხმდები ადრესატთან. მაგალითად, ყოველი ასო წაიწევს სამით. მესამე პირი სიტყვებს ვერ აღიქვამს, მაგრამ თუ ხშირად გამოყენებული ტაქტიკები იცის, შეუძლია სხვადასხვა ვერსია სცადოს და შიფრი "გატეხოს".  


<!-- n -->

### სიმეტრიული - პაროლი
- რითიც შიფრავ/იმით ხსნი
- მესიჯს თუ გააგზავნი, სხვამ პაროლი უნდა იცოდეს - **vulnerability**

<!-- n -->

ამ მიზეზით, მარტივი დაშიფვრა უსაფრთხოებისთვის არ გამოდგება. ალგორითმის გარდა, აუცილებელია იყოს რაღაც დამატებითი, **ინდივიდუალური**. ისე, რომ თუნდაც სხვამ გაიგოს რომელ ალგორითმს იყენებ დასაშიფრად, ვერ შეძლოს გატეხვა.

ამის პარალელისთვის შეგვიძლია წარმოვიდგინოთ, რომ ჩვენ და წერილის ადრესატს გვაქვს გასაღები კონკრეტული ყუთისთვის. ჩვენ გზავნილს ვდებთ ყუთში, ვკეტავთ გასაღებით, ხოლო ადრესატი ასეთივე გასაღებით ხსნის.

_რა პრობლემას ხედავ ასეთ პრინციპში?_

გასაღების უსაფრთხოდ მიწოდება ადრესატისთვის რთული, ზოგ შემთხვევაში კი შეუძლებელია. თუ პაროლზე პირადად არ შეთანხმდებით, მაშინ **დაშიფვრის გარეშე მოგიწევს მისი გაგზავნა**, და თუ მესამე პირმა პაროლი გზაში ხელში ჩაიგდო, მომავალი კომუნიკაცია დაუცველია. ანალოგი იქნებოდა დაულუქავი კონვერტით გასაღების გაგზავნა - გზაში მისი ასლის გაკეთება მარტივია.

### ასიმეტრიული
- public/private pair
- ანალოგი: უგზავნი ბოქლომს, მაგრამ გასაღები მხოლოდ შენ გაქვს

<!-- n -->
ამ პრობლემასთან გასამკლავებლად

## Privacy  


## თავდაცვა
### https (secure http)
![][image-2]

<!-- n -->
https პროტოკოლის დროს, სერვერსა და ბრაუზერს ერთმანეთთან კომუნიკაცია **ასიმეტრიული დაშიფვრით ** აქვთ. როდესაც საიტზე შესვლა (ანუ საიტის html-ის გადმოწერა) გინდა, ბრაუზერი ჯერ იგებს სერვერის საჯარო გასაღებს, და მისი მეშვეობით შიფრავს მოთხოვნას. სერვერი პირადი გასაღების მეშვეობით ხსნის შიფრს მოთხოვნას. შედეგად, მესიჯის ან სურათის გაგზავნისას, wifi ქსელი და isp მხოლოდ გაურკვეველ რიცხვებს ხედავენ. ამავენაირად, სერვერსაც აეგზავნება ბრაუზერის საჯარო გასაღები, და მისგან მოსული პასუხი ისეა დაშიფრული, რომ მხოლოდ შენს ბრაუზერს შეუძლია გაიგოს, რა არის გამოგზავნილი.

თუ საიტი http-ს არ იყენებს, შენს isp-ს და wifi ქსელის სხვა წევრებს ასევე წვდომა აქვთ შენს**ყველა გაგზავნილ/მიღებულ ინფორმაციაზე** (პირადი მესიჯების ჩათვლით). თანამედროვე ბრაუზერები გაფრთხილებენ ასეთ საიტზე შესვლისას - ჩნდება "your connection is not secure" მესიჯი, რომლისთვის გვერდის ასავლელი ღილაკი რამდენიმე მენიუს იქითაა დამალული.

### Unique Passwords

### Password Managers
- google and third party android developers
- apple keychain
- bitwarden
- Firefox users
<!-- n -->
მარტივი გასაგებია, რამხელა საფრთხეს შეიცავს ერთი პაროლის ბევრგან გამოყენება.  თუმცა, ამ პრინციპის შესრულება დახმარების გარეშე შეუძლებელია - აბსურდია ადამიანს უამრავ საიტზე სხვადასხვა პაროლების დაყენება მოთხოვო. ამიტომ ეს პაროლები სადღაც უნდა შევინახოთ - თუმცა ისინიც დაცული (დაშიფრული) უნდა იყოს. პროგრამები იყენებენ ე.წ. master key-ს - მთავარ, მნიშვნელოვან პაროლს. პაროლის მენეჯერები ამ მიზნისთვის გამოიყენება, და თუ მათით არ სარგებლობ, ე.ი. ყველგან ერთი პაროლი გაქვს და შენი სენსიტიური მონაცემების მოპოვებას ნებისმიერი მსურველი შეძლებს - სუსტად დაცული ან დაუცველ საიტებზე შეღწევით, პაროლის გაგების და სენსიტიურ საიტზე გამოყენებით.

### Multi Factor Authentication
- სანდო მოწყობილობები
- ახალ მოწყობილობაზე დამატებითი ვერიფიკაცია
- ვერიფიკაციის კოდი არის დროებითი
<!-- n -->
ამ პრინციპის იდეა ისაა, რომ სენსიტიური სისტემები (სოციალური მედიის პროფილი, მეილი, პირადი ფაილები) მომხმარებლის პაროლის გაგების შემთხვევაშიც კი უსაფრთხოდ დარჩეს. დამატებითი იდენთიფიკაცია, როგორ წესი, ერთჯერადი sms კოდის საშუალებით ხდება.

#### მაგალითები
- google/facebook 2FA
- 3D Secure Payments
- banking mobile/web app login

<!-- n -->
ხშირად, ვერიფიკაციის კოდს დამატებითი ინფორმაცია მოყვება - მაგალითად, ინტერნეტ გადახდისას 3D secure კოდი როდესაც მოგდის, მითითებულია საიტი და თანხის რაოდენობა, რომ ბრაუზერის კომპრომისის შემთხვევაშიც კი უზრუნველყოფილი იყოს უსაფრთხოება. მაგალითად, დააყენე რაღაც extension, რომელიც გადახდის გვერდზე ჯავასკრიპტით ცვლის თანხის რაოდენობას, უფრო ნაკლებს გიჩვენებს, სინამდვილეში კი მეტი თანხის ჩამოჭრას თანხმდები.


### Data - ბრმა ნდობა ან Open Source
მნიშვნელოვანია ყოველთვის, გვახსოვდეს, რომ დახურული აპლიკაციების უმეტესობის "უსაფრთხოება" მხოლოდ ცარიელი, გარანტიის გარეშე მოცემული პირობაა - ჩვენს მოწყობილობაზე მოდის მხოლოდ ორობითი კოდი პროცესორისთვის, და მისგან აზრის გამოტანა შეუძლებელია. მათი სერვერები კი დახურულია და წარმოდგენა არ გვაქვს სინამდვილეში რისთვის გამოიყენება ჩვენი მონაცემები. 

პერსონალური კომპიუტერების გაჩენიდან არსებობს მოძრაობა ასეთი პროგრამების წინააღმდეგ - Open Source/Free Software Movement. ამ ფილოსოფიის მიმდევრებისთვის მნიშვნელოვანია კოდის საჯაროობა და თავისუფლება - მათი შეხედულებით, მომხმარებელს აქვს **ფუნდამენტური** უფლება, იცოდეს რას აკეთებს პროგრამის კოდი.


<!--
### Zero trust encryption


TODO:

## Privacy/Tracking
### 3rd Party Scripts
### Data Sharing
### Cookies
### Ghost Profiles


Cookies (privacy, თავდაცვა)

- pgp
-->

[image-1]:	https://img.wattpad.com/2193998f1b3aba21754ec39bdb499721f952f358/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f776174747061642d6d656469612d736572766963652f53746f7279496d6167652f346351396b524557764a61366c673d3d2d3631373338373637382e313534613732333164333733386633313238343839313432373431392e6a7067?s=fit&w=720&h=720
[image-2]:	data:image/png;base64,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