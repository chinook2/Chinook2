This document describe coding conventions used by the Chinook development team for client side.

## General rules

All files are encoded in UTF-8

Names of javascript files start with an uppercase  
` Action.js `

## Code rules

In a string exempt from quotation mark you must use quotes to enclose the string. If they are quote you use apostrophe and if they are both use quote
``` Javascript
var foo = "It's a stupid rule";
var bar = 'You said "stupid"?'
var foobar = "Yes, I said \"It's a stupid rule\"";
```
<br/>

They are space on both side of comparison and affectation
``` Javascript
if(foo == "N") {}
```
<br/>

Loop et conditionnal blocks observe this structure
``` Javascript
if(boolVar) {
	doSomething();
} else {
	doAnotherThing();
}

for(var i = 0; i < 10; i++) {
	loopAction();
}
```
