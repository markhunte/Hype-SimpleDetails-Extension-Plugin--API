<p>NEW DJ CARDS.</p>

<h2 id="toc_0">Intent:</h2>

<h2 id="toc_1">Using: Custom HypeSimple Descriptions Function.</h2>

<p>The custom version of this allows us to add an image of the Dj.
Initially, the attempt was to include an inline image block in the  css ::before.
This did not work well. So we now include a div wrapper and an image block along with the  construction of the detail.’s block. </p>

<p>The div wrapper and image are above the detail block. 
The image  path is passed in via the constructor.</p>

<p>We also have are not  using the <strong>::before</strong> content in this custom version to place the** <strong>leadingText</strong>.  This is now a <code>&lt;p&gt;</code> block.</p>

<p>The leadingText  path is passed in via the constructor,  and placed in the <code>&lt;p&gt;</code> block directly.</p>

<pre><code> descriptionElement_child.innerHTML = `
&lt;div class=“_wrap”&gt;  &lt;img src=“${image_}” alt=“Girl in a jacket” style=“clip-path: circle(50%); shape-outside:circle(39%);  box-sizing: border-box; margin-right:3rem; float:left;width:100px; height:auto;”&gt; &lt;p class=“def” style=“color: ${leadingTextColor};font-size:${fontSize}; word-wrap: break-word;white-space: pre-line;padding-left:20px;”&gt;${sourceDescription_20}&lt;/p&gt;

 &lt;/div&gt;

      &lt;details  id=“${summaryClass}” class=“details_” data-autoclose=“${acceptsAutoClose}”&gt;
        &lt;summary class=“${summaryClass}” style=“;float:right;color: ${leadingTextColor}; font-size:${fontSize};”&gt;&lt;/summary&gt;
        &lt;p class=“def” style=“color: ${followingTextColor};font-size:${fontSize};”&gt;${sourceDescriptionMore}&lt;/p&gt;
      &lt;/details&gt;
    `;
</code></pre>

<p>In the  load() , we  take all the text (objects)  that need to go into this area and calculate the word count simply using split. We then pass that in as the  <strong>splitTextAtWordNumber</strong> so we only have the correct text go into the ::after as the followingText.
There are also additions and deletions in the CSS blocks to adjust all of the above. Along with some inline styling for the image.</p>

<p>We are also passing in the dj sort order and loading it in data-sort order, to use later on in the JQuery Animation’s Array  for the float left’s sort order.</p>

<hr>

<h2 id="toc_2">Using: Clone function.</h2>

<p><em>Intent: Try to have all the dis show at the same time, hall of fame if you will.</em></p>

<p>The new code clones the original DJ card ( not populated in the final result)
The clones are created, then populated.</p>

<hr>

<h2 id="toc_3">Using jQuery Animate():</h2>

<p>Intent: I want control the cards layout in a row and column order. 
<img src="Screenshot%202023-10-11%20at%2020.53.36.png" alt="Screenshot 2023-10-11 at 20.53.36">
I am using the same JQuery animate  blocks I used in the Filter Tags  project for a Tumult post  ( with some adjustments ). This was a much simpler way of doing the layout for the cards than trying to get the clone functions to do it. The animate  function is called after the population of the cards at the end of the load() function. The added bonus is we get the really nice float left animation of the cards.</p>

<p><strong>( NOTE: It may be worth merging the Clone and Animation code into one extension. )</strong></p>

