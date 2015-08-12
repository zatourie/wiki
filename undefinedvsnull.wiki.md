
```
<html>
<head>
<script type="text/javascript">
try{
    trace(a);            //undefined
    trace(typeof a); //undefined
    var a;
    trace(a);            //undefined
    trace(typeof a);  //undefined
    a = 1;
    trace(a);            //1
    trace(typeof a);  //number
    a = null;
    trace(a);            //null
    trace(typeof a);  //object

    b = null;
    trace(b);           //null
    trace(typeof b); //object

    a = 1;
    b = 2;

    trace(window.a); 
    trace(this.a);
    trace(a);

    trace(window.b);
    trace(this.b);
    trace(b);


    trace(delete a); //false
    trace(a);           //1
    trace(delete b); //true
    trace(b);           //b is not defined
}catch(e){
    trace(e.message);
}

function trace(msg){
    try{console.log(msg);}catch(e){/*do nothing*/}
}
</script>
</head>
<body></body>
</html>
```