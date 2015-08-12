jQuery 개발자 John Resig의 Simple "Class" Instantiation 을 읽어봅시다.


http://ejohn.org/blog/simple-class-instantiation/

```
/*Classical way*/
function Person(){
    this.name = "noname";
    this.get_name = function (){
        return this.name;
    }
    this.set_name = function(arg){
        this.name = arg;
    }
}

var p1 = new Person(); //this links to Person object
p1.set_name("Minkyu");
console.log(p1.get_name());

p1.name = "바보"; //accessable and modifiable at runtime
console.log(p1.name); //accessable and modifiable at runtime
console.log(p1.get_name());

var p2 = Person(); //Initiate without new, this links to Window, a disaster has just occured here!!!
console.log(p2); //undefined because Person function has no return
console.log(this.name); //Ooooooooops!
console.log(this.get_name()); //noname???


/*Better way*/
function person(){
    var name; //encapsulated local variable
    return {
        get_name : function(){
            return this.name;
        },
        set_name : function(name){
            this.name = name;
        }
    };
}

var p3 = person();
console.log("p3");
console.log(p3);
var p4 = person();

console.log(p3.get_name()); //undefined
p3.set_name("Minkyu");
console.log(p3.get_name()); //Minkyu

console.log(p4.get_name()); //undefined
p4.set_name("Hello");
console.log(p4.get_name()); //Hello


var p5 = new person(); //invoked with new!!!
console.log(p5);

console.log(p5.get_name()); //undefined
p5.set_name("World");
console.log(p5.get_name()); //World

```

```
/*Javascript Modular Pattern*/
var Module = (function(){
    var privateProperty = 'foo';
    
    function privateMethod(args){
        // do something
    }

    return {

        publicProperty: "",

        publicMethod: function(args){
            // do something
        },

        privilegedMethod: function(args){
            privateMethod(args);
        }
    }
})();
```