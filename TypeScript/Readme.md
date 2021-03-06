<div dir="rtl">

# Introduction   

زبان TypeScript یک سوپر‌ست نوع‌گذاری شده از JavaScript است که به زبان JavaScript کامپایل می‌شود. به بیانی دیگر، TypeScript  همان JavaScript است برای توسعه در مقیاس کاربردی. این زبان به شما امکان می دهد JavaScript را همانطور که می خواهید بنویسید و خوانایی و رفع اشکال آن را بهبود می بخشد. این زبان یک زبان شی گرای خالص است و فریمورک های معروفی مانند Angular 2.0 به این زبان نوشته شده اند.

# Requirements

همان طور که گفته شد ابتدا باید برنامه نوشته شده در زبان Typescript را به زبان JavaScript کامپایل و سپس آن را نیز تفسیر کرد. پس به `nodeJs` و `type Script Compiler(tsc)` نیاز داریم. همچنین نصب `npm` نیز توصیه می شود.

# installation

برای نصب `nodejs` از دستور زیر استفاده می کنیم:

<div dir="ltr">
	
    sudo apt install nodejs
	
</div>

برای نصب `npm` از دستور زیر استفاده می کنیم:

<div dir="ltr">
	
    sudo apt install npm
	
</div>

برای نصب `tsc` نیز از `npm` استفاده می کنیم:

<div dir="ltr">
	
    npm install -g typescript
	
</div>

حال برای کامپایل و اجرای برنامه های این زبان مراحل زیر را طی می کنیم:

1.ابتدا فایل مورد نظر را با پسوند `ts.` ذخیره می کنیم (برای مثال `test.ts`)
	
2.سپس فایل مورد نظر را با دستور `tsc [file_name].ts` به زبان js کامپایل می کنیم.(خروجی آن یک فایل مانند `test.js` است)
	
3.در نهایت برای اجرای فایل نهایی دستور `node [file_name].js` را اجرا می کنیم.
	
همچنین پکیج هایی نیز وجود دارند که مراحل 2 و 3 را ترکیب می کنند.(مانند `ts-node`)

# Differences

تایپ‌اسکریپت دربرگیرنده جاوااسکریپت است ولی تفاوت‌هایی جزیی با آن دارد که در جدول زیر به آن‌ها می‌پردازیم:

| JavaScript | TypeScript |  |
| ---------- | ---------- | --------- |
| در نسخه های قدیمی موجود نبود | استفاده از کلاس، اینترفیس، تایپ | شی‌گرایی
| وجود ندارد | با استفاده از تایپ و اینترفیس | Data binding | 
پکیج‌ها بدون نیاز به بیلد قابل استفاده هستند|پکیج‌های گوناگونی را با استفاده از npm می‌توان نصب کرد|پکیج‌های مختلف
چنین ویژگی وجود ندارد|می‌توان از Prototyping استفاده کرد|Prototyping
کدها کامپایل نمی‌شوند|کدها کامپایل می‌شوند|کامپایل
چنین ویژگی وجود ندارد|می‌توان از Annotation استفاده کرد|Annotation

- درنسخه‌های قدیمی js، شی‌گرایی وجود نداشت ولی در نسخه جدید به آن اضافه شده ولی با ts دارای تفاوت‌هایی است که در قطعه کد زیر به آن می‌پردازیم:

<div dir="ltr">
	
   	// JS🟨
	class User {
	    #name
	    constructor(name) {
	        this.#name = name;
	    }
	}
	const user = new User('Tom');
	
	// TS🟦
	class User {
	    #name: string 
	    constructor(name: string) {
	        this.#name = name;
	    }
	}
	const user = new User('Tom')

	
</div>

تنها تفاوت در تعریف متغیر name است که در ts باید نوع آن‌را مشخص کرد.

- در ts می‌توان داده‌ها را با ساختار خاصی ساخت. اینکار به وسیله‌ type و interface امکان‌پذیر است که در بخش‌های بعدی به آن‌ها اشاره می‌شود.

- در ts کد ابتدا به زبان js کامپایل و سپس اجرا می‌شود. برای همین اگر اروری داشته باشد قبل از اجرای کد باید آن‌را رفع کرد. به مثال زیر توجه کنید:

<div dir="ltr">

TS:

</div>

<div dir="ltr">

    s = "ali";
    console.log(s); // error s not defined
    s = 12;
    console.log(s); // error s not defined

</div>

<div dir="ltr">

Js:

</div>

<div dir="ltr">

    s = "ali";
    console.log(s); //ali
    s = 12;
    console.log(s); //12

</div>

- در ts ما برای annotation به شکل زیر عمل میکنیم:

<div dir="ltr">

    var variableName: TypeAnnotation = value;  

</div>

مثلا: 

<div dir="ltr">

    var age: number = 44;         // number variable  
    var name: string = "Ali";     // string variable  


</div>

اگر در ادامه به متغیر name مقداری عددی تخصیص دهیم به ارور میخوریم ولی در js این ویژگی وجود ندارد.

<div dir="ltr">

    // JS🟨
    var name = “Ali”;
    name = 44 ; // valid

    // TS🟦
    var name = “Ali”;
    name = 44 ; // error



</div>

# TypeScript basic syntax

برخی نکات اولیه در سینتکس TypeScript:

- semicolon در TypeScript اختیاری است. هر دستور در TypeScript یک عبارت نام دارد. یک خط می‌تواند شامل چندین دستور باشد به شرطی که دستورات توسط semicolon از یکدیگر جدا شده باشند.

- TypeScript، حساس به بزرگی حروف است.

- TypeScript یک زبان Object Oriented است. اشیا در این زبان سه feature اصلی دارند:

	1. State
	2. Behavior
	3. Identity

- کامنت در TypeScript بصورت زیر گذاشته میشوند:

<div dir="ltr">

    //this is single line comment 
	 
    /* This is a  
    Multi-line comment 
    */

</div>

- برای پرینت یک پیام از سینتکس زیر استفاده میشود:

<div dir="ltr">
	
    console.log("hello world")
    
</div>

# type

- Any: دیتا تایپ “Any” سوپر همه ی تایپ هاست و بصورت داینامیک یک تایپ را مشخص میکند. 
- Built-in types: 

	-تفاوت Null و Undefined: متغیری که در ابتدا undefined مشخص شده یعنی مقدار یا شی ای به آن اختصاص داده نشده است ولی متغیر null به معنی آن است که به این متغیر شی ای که مقداری ندارد اختصاص داده شده است.

- User-defined types

![enter image description here](https://www.tutorialspoint.com/typescript/images/data_types.jpg)

# variable

متغیر ها در TypeScript بصورت زیر تعریف میشوند:

![enter image description here](https://www.tutorialspoint.com/typescript/images/declare_type.jpg)

در این تعریف بخش type-annotation و value اختیاری است و میتوانند در تعریف مشخص نشوند.
مثال:

<div dir="ltr">
	
    var score: number = 50;
    
</div>

# Condition و Loop

-نمونه کد برای تصمیم گیری در یک Condition:

<div dir="ltr">
	
    if (num % 2==0) { 
        console.log("Even"); 
    } else {
        console.log("Odd"); 
    }
    
</div>

۳ روش برای ایجاد حلقه در جهت اجرای چند باره یک بخش از کد وجود دارد:

- for loop:

<div dir="ltr">
	
    for (initial_count_value; termination-condition; step) {
        //statements 
    }
    
</div>
    
- while loop:

<div dir="ltr">
	
    while(condition) { 
        // statements if the condition is true 
    }

</div>

- do… while:

<div dir="ltr">
	
    do {
        //statements 
    } while(condition)
    
</div>	

# Function

فانکشن شامل یک سری عبارت است تا یک تسک خاص را انجام دهند. فانکشن درواقع یک بلوک منطقی برای مرتب سازی کد است. برای دسترسی به کد این بلوک فانکشن را صدا میزنیم که به این ترتیب کد reusable میشود.

سینتکس فانکشن به صورت زیر است:

<div dir="ltr">

    function func_name( param1 [:datatype], param2 [:datatype]…) { 
        // function body   
    }

</div>

که وجود پارامتر ها اختیاری است.

همچنین سینتکس برای صدا زدن یک فانکشن بصورت زیر است:

<div dir="ltr">

    function_name(param1 , param2…)

</div>

-یک نمونه کد برای ایجاد یک فانکشن و صدا زدن آن:

<div dir="ltr">

    function disp_details(id, name, mail_id) {
        console.log("ID:", id);
        console.log("Name", name);
	
    if (mail_id != undefined)
        console.log("Email Id", mail_id);
    }
    disp_details(123, "John");

</div>

### توابع بازگشتی:

تابع بازگشتی روشی برای تکرار یک عمل به طریقی است که یک فانکشن بتواند خودش را صدا بزند.

-یک نمونه کد برای ایجاد یک تابع recursive و صدا زدن آن:

<div dir="ltr">

    function factorial(number) {
        if (number <= 0) {         // termination case
            return 1; 
        } else {     
            return (number * factorial(number - 1));     // function invokes itself
        } 
    }; 
    console.log(factorial(6));      // outputs 720 

</div>

# Numbers

TypeScript مانند JavaScript مقادیر عددی را بصورت اشیا از حنس عدد ساپورت میکند. شی Number یک مقدار عددی را به یک نمونه از کلاس Number تبدیل میکند و این کلاس برای آن مثل یک wrapper عمل میکند.

-سینتکس مناسب برای ساختن یک Number Object:

<div dir="ltr">

    var var_name = new Number(value)

</div>

-بعضی از property های شی Number در زیر لیست شده اند:

- MAX_VALUE: بزرگ ترین عددی که در این زبان امکان وجودش هست. 
- MIN_VALUE: کوچک ترین عددی که در این زبان امکان وجودش هست. 
- NaN: نشان دهنده مقداری است که از جنس عدد نیست. (Not a Number) 

-در صورتی که یک مقدار غیر عددی به constructor شی Number پاس داده شود constructor، NaN برمیگرداند.

-برخی method های شی Number در زیر لیست شده اند:

- ()toExponential: این متد یک رشته برمیگرداند که نمایش عدد به فرم نمایی است.
- ()toPrecision: این متد عدد را با دقت مشخص شده (تعداد ارقام با اهمیت) نشان میدهد.
- ()toString: با ورودی گرفتن یک پایه، عدد را در مبنای مشخص شده بصورت رشته برمیگرداند.
- ()valueOf: مقدار primitive عدد را برمیگرداند.

# Strings

شی String مقدار primitive رشته را همراه با تعدادی method کمکی، در برمیگیرد.

-سینتکس برای ایجاد یک شی String:

<div dir="ltr">

    var var_name = new String(string);

</div>

-یک مثال کد از کاربرد این شی همراه با متد دسترسی به طول رشته:


<div dir="ltr">
    var uname = new String("Hello World") 
    console.log(uname) 
    console.log("Length "+uname.length) 
</div>

-برخی method های شی String در زیر لیست شده اند:

- ()charAt: کاراکتر موجود در شاخص مشخص شده را برمیگرداند.
- ()concat:متن دو رشته را با هم پیوند میزند و یک رشته جدید برمیگرداند.
- ()search: یک عبارت را در یک رشته جست و جو میکند.
- ()split: یک شی String را تقسیم کرده و بصورت یک آرایه از رشته ها برمیگرداند.
- ()replace: یک زیر رشته از رشته را با یک زیر رشته دیگر جایگزین میکند.
- ()substr: یک زیر رشته کاراکتر را که از شاخص مشخص شده شروع شده اند و تا تعداد مشخص شده پیش رفته است را برمیگرداند.
- ()toLowerCase: کاراکتر های رشته را به حروف کوچک تبدیل میکند و برمیگرداند.
- ()toUpperCase: کاراکتر های رشته را به حروف بزرگ تبدیل میکند و برمیگرداند.
- ()toString: یک رشته برمیگرداند که شی را نمایش بدهد.
- ()valueOf: مقدار رشته را برمیگرداند.

# Array

آرایه یک مجموعه از value ها را ذخیره میکند.

<div dir="ltr">

    var array_name[:datatype];        //declaration 
    array_name = [val1,val2,valn..]   //initialization

</div>

برخی از method هایی که در TypeScript برای آرایه وجود دارند در زیر لیست شده اند:

- ()concat

	یک آرایه جدید شامل جوین شده آرایه با یک آرایه دیگر را برمیگرداند.

- ()filter

	یک آرایه جدید برمیگرداند که با شرایط ذکر شده فیلتر شده اند.

- ()forEach

	یک فانکشن را برای همه المنت های آرایه صدا میزند.

- ()indexOf

	شاخص اولین المنت آرایه برابر با مقدار مشخص شده را برمیگرداند یا اگر چنین المنتی در آرایه موجود نباشد ۱- را برمیگرداند.

- ()pop

	آخرین المنت آرایه را حذف میکند و آن را برمیگرداند.

- ()push

	یک یا چند المنت جدید را به آخر آرایه اضافه میکند و طول جدید آرایه را برمیگرداند.

- ()sort

	المنت های آرایه را مرتب و سورت میکند.
	
# Tuples

Tuple ها برای زمانی که احتیاج داریم یک مجموعه از مقادیری با انواع مختلف ذخیره کنیم به کار میآیند زیرا آرایه ها این کار را نمیتوانند انجام بدهند.

-سینتکس برای تعریف یک tuple:

<div dir="ltr">

    var tuple_name = [value1,value2,value3,…value n]

</div>

-مثال:

<div dir="ltr">
	
    var mytuple = [10,"Hello"];
    
</div>

دسترسی به اعضای tuple هم به شکل زیر صورت میگیرد:

<div dir="ltr">
	
    var tup = [] 
    tup[0] = 12 
    tup[1] = 23 
    
</div>

-دو تا از عملگر هایی که روی یک tuple قابل انجام است در زیر توضیح داده شده اند:

- ()Push: یک عضو به tuple اضافه میکند.
- ()Pop: عضو آخر tuple را حذف میکند و آن را برمیگرداند.

-تخریب ساختار tuple: به این معنا که ساختار بندی آن را از بین میبریم. 

-مثالی از تخریب ساختار یک tuple:

<div dir="ltr">
	
    var a =[10,"hello"] 
    var [b,c] = a 
    console.log( b )   //10 
    console.log( c )   //hello
    
</div>

# Union

TypeScript این قابلیت را به برنامه میدهد که یک یا چند تایپ را با هم ترکیب کند. تایپ Union یک روش برای نشان دادن این است که یک مقدار میتواند یکی از چند تایپ ذکر شده را داشته باشد.

-سینتکس برای نشان دادن تایپ Union:

<div dir="ltr">

    Type1|Type2|Type3 

</div>

-یک مثال از تعریف متغیر با استفاده از Union:

<div dir="ltr">

    var val:string|number 
    val = 12 
    console.log("numeric value of val "+val) 
    val = "This is a string" 
    console.log("string value of val "+val)

</div>

-یک مورد استفاده دیگر union type ها به عنوان پارامتر فانکشن هاست:

<div dir="ltr">

    function disp(name:string|string[]) { 
        if(typeof name == "string") { 
            console.log(name) 
        } else { 
            var i; 
      
            for(i = 0;i<name.length;i++) { 
                console.log(name[i])
            } 
        } 
    } 

</div>

Union تایپ ها همچنین میتوانند در آرایه ها یا اینترفیس ها مورد استفاده واقع شوند:

<div dir="ltr">

    var arr:number[]|string[]; 
    var i:number; 
    arr = [1,2,4] 
    console.log("**numeric array**")  

    for(i = 0;i<arr.length;i++) { 
        console.log(arr[i]) 
    }  

    arr = ["Mumbai","Pune","Delhi"] 
    console.log("**string array**")  

    for(i = 0;i<arr.length;i++) { 
        console.log(arr[i]) 
    } 

</div>

در این قطعه کد اعضای آرایه میتوانند از نوع رشته یا عددی باشند.

# Interface

اینترفیس ها شامل ۳ بخش زیر هستند:

1. properties
2. methods
3. events

اینترفیس ها فقط این اعضا را declare میکنند و define کردن این اعضا بر عهده کلاسی است که آن را پیاده سازی میکند.

-روش تعریف اینترفیس:

<div dir="ltr">

    interface interface_name { 
        ...
    }

</div>

-یک مثال از تعریف و پیاده سازی یک اینترفیس توسط یک کلاس:

<div dir="ltr">

    interface IPerson { 
        firstName:string, 
        lastName:string, 
        sayHi: ()=>string 
    } 

    var customer:IPerson = { 
        firstName:"Tom",
        lastName:"Hanks", 
        sayHi: ():string =>{return "Hi there"} 
    } 

</div>

# Class

TypeScript درواقع همان JavaScript است که شی گرایی را ساپورت میکند. یک کلاس در TypeScript، داده های یک شی را محصور میکند. برای تعریف یک کلاس از سینتکس زیر استفاده میکنیم:

<div dir="ltr">
	
    class class_name {
        //class scope 
    }

</div>

یک کلاس میتواند ۳ بخش زیر را شامل شود:

1. Fields
2. Constructors
3. Functions

-یک مثال از یک کلاس که شامل هر ۳ این اعضا است در زیر آمده است:

<div dir="ltr">

    class Car { 
        //field 
        engine:string; 
 
        //constructor 
        constructor(engine:string) { 
            this.engine = engine 
        }  

        //function 
        disp():void { 
            console.log("Engine is  :   "+this.engine) 
        } 
    }

</div>

# Object

یک object یک نمونه است که شامل مجموعه ای از کلید ها و مقدار هاست. این مقدار ها میتوانند عددی، فانکشن یا حتی آرایه از شی های دیگر باشند.

- سینتکس object بصورت زیر است:

<div dir="ltr">

    var object_name = { 
        key1: “value1”, //scalar value 
        key2: “value”,  
        key3: function() {
             //functions 
        }, 
        key4:[“content1”, “content2”] //collection  
    };

</div>

-یک نمونه کد برای تعریف یک object و دسترسی به اعضای آن:

<div dir="ltr">

    var person = { 
        firstname:"Tom", 
        lastname:"Hanks" 
    }; 
    //access the object values 
    console.log(person.firstname) 
    console.log(person.lastname)

</div>

همچنین در صورتی که بخواهیم مقادیری را به object اضافه کنیم. TypeScript با استفاده از تعریف یک method template این اجازه را به ما میدهد. مثلا در قطعه کد زیر ما یک فانکشن را به شی person اضافه میکنیم:

<div dir="ltr">

    var person = {
        firstName:"Tom", 
        lastName:"Hanks", 
        sayHello:function() {  }  //Type template 
    } 
    person.sayHello = function() {  
        console.log("hello "+person.firstName)
    } 

</div>

</div>
