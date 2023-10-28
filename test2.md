NEW DJ CARDS.

## Intent:


## Using: Custom HypeSimple Descriptions Function.

The custom version of this allows us to add an image of the Dj.
Initially, the attempt was to include an inline image block in the  css ::before.
This did not work well. So we now include a div wrapper and an image block along with the  construction of the detail.’s block. 

The div wrapper and image are above the detail block. 
The image  path is passed in via the constructor.
We would normally split the text so we have some before the disclosure button and some after. Leading text and following text.
Here we are  not  using the **::before** content in this custom version to place the** **leadingText**.  This is now a `<p>` block.

The leadingText  (sourceDescription_20) is passed in via  the fulltext in the constructor and split from the following text ,  and placed in the `<p>` block directly and  along side the image.
   
```
 descriptionElement_child.innerHTML = `
<div class=“_wrap”>  <img src=“${image_}” alt=“Girl in a jacket” style=“clip-path: circle(50%); shape-outside:circle(39%);  box-sizing: border-box; margin-right:3rem; float:left;width:100px; height:auto;”> <p class=“def” style=“color: ${leadingTextColor};font-size:${fontSize}; word-wrap: break-word;white-space: pre-line;padding-left:20px;”>${sourceDescription_20}</p>

 </div>

      <details  id=“${summaryClass}” class=“details_” data-autoclose=“${acceptsAutoClose}”>
        <summary class=“${summaryClass}” style=“;float:right;color: ${leadingTextColor}; font-size:${fontSize};”></summary>
        <p class=“def” style=“color: ${followingTextColor};font-size:${fontSize};”>${sourceDescriptionMore}</p>
      </details>
    `;
```

We fetch the data in the load() function and parse the csv text in to json.
Within the load() function we then call back to the djsUpdate() which in turn 
calls the  doClone_()  

This is done  for each   dj object.


```javascript
djs.forEach((adj, index) => {
	
	hypeDocument.functions().doClone_(hypeDocument, adj, event)
	
	});
```

The float()  hype function is called at the end of the doClone_() .

 Because we are not using the ::before   for the **leadingText**, we still need the ::before’s calculated  space to be accounted for in the DOM, otherwise it will not render correctly and the card will be too small.
 In the  doClone_() , we  take all the text (objects)  that need to go into the leadingText and followingText area sand calculate all their word counts simply using split. We then pass that in as the  **splitTextAtWordNumber** .

 We only have the (about) text go into the ::after as the followingText. 
 And get the calculated spacing above and before the show more button where we can layer the DJ Show details in it’s <p> block.
There are also additions and deletions in the CSS blocks to adjust all of the above. Along with some inline styling for the image.

 We are also passing in the dj sort order and loading it in data-sort order, to use later on in the Animation’s Array  for the float left’s sort order.



***
## Using: Clone function.
*Intent: Try to have all the DJs show at the same time, hall of fame if you will.*

The new code clones the original blank DJ card which itself not populated in the final result and is hidden off viewport.
The clones are created, then populated.
***

## Using jQuery Animate():
Intent: I want control the cards layout in a row and column order. 
![Screenshot 2023-10-11 at 20.53.36](Screenshot%202023-10-11%20at%2020.53.36.png)
I am using the same JQuery animate  blocks I used in the Filter Tags  project for a Tumult post  ( with some adjustments ). This was a much simpler way of doing the layout for the cards than trying to get the clone functions to do it. The animate  function is called after the population of the cards at the end of the load() function. The added bonus is we get the really nice float left animation of the cards.

**( NOTE: It may be worth merging the Clone and Animation code into one extension. )**
**( NOTE: 2** We can use native Hype set properties , see new hype file., update above

