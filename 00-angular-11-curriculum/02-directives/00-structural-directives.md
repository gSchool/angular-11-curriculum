# Structural directives

In [this video](https://drive.google.com/file/d/1Cac-KxqgP1tcf5Qnb21sSgcKZX66rY81/view) in the 
[lesson on iteration](../01-http/04-iterating-over-objects.md), we talked about *structural directives*.  

You may recall this construct, where _flights_ is an array of objects, and we use an *ngFor* structral directive to loop through the flights: 

```
<div *ngFor="let flight of flights">
    {{flight.origin}}, {{flight.destination}}, {{flight.nonstop}}
</div>

```

We have been using the term *structural directive*, but what does this really mean ?

A *structural directive* in Angular is a piece of code that 



