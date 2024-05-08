# single responsibility principles

Single responsibility principle keeps your code organized and understandable by making each function only have one responisbility. 

## execution

We added single responsibility principles by adding comments before the code to explain the function of it so others could also understand our intent. 

When fixing the hitboxes, our team used single responibility principles to explain the code and its function. 

<pre>
<code>
const tolerance = 10; // Adjust as needed
// Determine if this object's bottom exactly aligns with the other object's top
const onTopofPlatform = Math.abs(thisBottom - otherRect.top) <= tolerance;
</code>
</pre>
