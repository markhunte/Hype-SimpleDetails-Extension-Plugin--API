  <p>NEW DJ CARDS.</p>

<h2 id="toc_0">Intent:</h2>

<h2 id="toc_1">Using: Custom HypeSimple Descriptions Function.</h2>

<p>The custom version of this allows us to add an image of the Dj.
Initially, the attempt was to include an inline image block in the  css ::before.
This did not work well. So we now include a div wrapper and an image block along with the  construction of the detail.’s block. </p>

<p>The div wrapper and image are above the detail block. 
The image  path is passed in via the constructor.
We would normally split the text so we have some before the disclosure button and some after. Leading text and following text.
Here we are  not  using the <strong>::before</strong> content in this custom version to place the** <strong>leadingText</strong>.  This is now a <code>&lt;p&gt;</code> block.</p>

<p>The leadingText  (sourceDescription_20) is passed in via  the fulltext in the constructor and split from the following text ,  and placed in the <code>&lt;p&gt;</code> block directly and  along side the image.</p>

<pre><code> descriptionElement_child.innerHTML = `
&lt;div class=“_wrap”&gt;  &lt;img src=“${image_}” alt=“Girl in a jacket” style=“clip-path: circle(50%); shape-outside:circle(39%);  box-sizing: border-box; margin-right:3rem; float:left;width:100px; height:auto;”&gt; &lt;p class=“def” style=“color: ${leadingTextColor};font-size:${fontSize}; word-wrap: break-word;white-space: pre-line;padding-left:20px;”&gt;${sourceDescription_20}&lt;/p&gt;

 &lt;/div&gt;

      &lt;details  id=“${summaryClass}” class=“details_” data-autoclose=“${acceptsAutoClose}”&gt;
        &lt;summary class=“${summaryClass}” style=“;float:right;color: ${leadingTextColor}; font-size:${fontSize};”&gt;&lt;/summary&gt;
        &lt;p class=“def” style=“color: ${followingTextColor};font-size:${fontSize};”&gt;${sourceDescriptionMore}&lt;/p&gt;
      &lt;/details&gt;
    `;
</code></pre>

<p>We fetch the data in the load() function and parse the csv text in to json.
Within the load() function we then call back to the djsUpdate() which in turn 
calls the  doClone_()  </p>

<p>This is done  for each   dj object.</p>

<pre><code class="language-javascript">djs.forEach((adj, index) =&gt; {
    
    hypeDocument.functions().doClone_(hypeDocument, adj, event)
    
    });
</code></pre>

<p>The float()  hype function is called at the end of the doClone_() .</p>

<p>Because we are not using the ::before   for the <strong>leadingText</strong>, we still need the ::before’s calculated  space to be accounted for in the DOM, otherwise it will not render correctly and the card will be too small.
 In the  doClone_() , we  take all the text (objects)  that need to go into the leadingText and followingText area sand calculate all their word counts simply using split. We then pass that in as the  <strong>splitTextAtWordNumber</strong> .</p>

<p>We only have the (about) text go into the ::after as the followingText. 
 And get the calculated spacing above and before the show more button where we can layer the DJ Show details in it’s <p> block.
There are also additions and deletions in the CSS blocks to adjust all of the above. Along with some inline styling for the image.</p>

<p>We are also passing in the dj sort order and loading it in data-sort order, to use later on in the Animation’s Array  for the float left’s sort order.</p>

<hr>

<h2 id="toc_2">Using: Clone function.</h2>

<p><em>Intent: Try to have all the DJs show at the same time, hall of fame if you will.</em></p>

<p>The new code clones the original blank DJ card which itself not populated in the final result and is hidden off viewport.
The clones are created, then populated.</p>

<hr>

<h2 id="toc_3">Using jQuery Animate():</h2>

<p>Intent: I want control the cards layout in a row and column order. 
<img src="Screenshot%202023-10-11%20at%2020.53.36.png" alt="Screenshot 2023-10-11 at 20.53.36">
I am using the same JQuery animate  blocks I used in the Filter Tags  project for a Tumult post  ( with some adjustments ). This was a much simpler way of doing the layout for the cards than trying to get the clone functions to do it. The animate  function is called after the population of the cards at the end of the load() function. The added bonus is we get the really nice float left animation of the cards.</p>

<p><strong>( NOTE: It may be worth merging the Clone and Animation code into one extension. )</strong>
<strong>( NOTE: 2</strong> We can use native Hype set properties , see new hype file., update above</p>
