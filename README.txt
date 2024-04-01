Feel free to contact j.roach1713@gmail.com with questions

Link to Access the webpage: https://automationwithinreach.github.io/

Other Helpful Links:

model-viewer API Documentation: https://modelviewer.dev/docs/index.html
model-viewer API Examples: https://modelviewer.dev/examples/augmentedreality/index.html
model-viewer API Github: https://github.com/google/model-viewer

Code Structure Overview:
The site is deployed via root/index.html which then references other resources in root to create the website.
See the comments in index.html for more information

Instructions:

Note: Line number references are based on the last index.html commit on Apr 1, 2024. All the comments in index.html pertinent to these instructions will be commented with the following format:

<!-- Comments ****************************************************** -->

	Relevant Code

<!-- *************************************************************** -->

How to change models:

- Add your model in the glb or gltf file format to the root/models directory

- Lines 122 to 140 all follow the same Format:  
  <option value="models/AWR-00096.glb">AWR-00096_Rails, Pairs with AWR-00097</option>

- To add or remove a model from the site simply add or delete a line with this format:
  <option value="path to model">Name of Model</option>

- Note: If your are changing the first model in the list then the path on line 66 will also need to be changed. 
<model-viewer id="dimension-demo" poster="awr-logo.png" loading="auto" reveal="auto" src="CHANGE TO NEW PATH"
	
How to change hotspots:

- Open this link and upload your model: https://modelviewer.dev/editor/

- In the ribbon click the pen. then at the bottom of the ribbon click hotspots and add the hotspots you want on your model.

- Find the <model-viewer> snippet which is the code at the top of the ribbon.

- After adding hotspots the snippet will include button classes similar to this: 
	<button class="Hotspot" slot="hotspot-1" data-position="0m 1m 0m" data-normal="-0m -0m 0m">
	<div class="HotspotAnnotation">Test</div>
	</button>

- In index.html there are few section where current hotspots exist that need to be edited. First find the button classes starting on line 90.

- Add the button classes from the snippet underneath the last hotspot on line 114. 

- Rename and number the hotspot's ID, class, and slot along with the annotation's ID to follow the nameing convention.

- Find the clearAnnotations() function on line 259 remember after adding the previous code this line number is no longer accuate.

- Add the following lines for each new hotspot:
	document.getElementById("spot-#").setAttribute('class', "hidden-hotspot");
		document.getElementById("ant-#").setAttribute('class', "hidden-annotation");

- Find the line containing: var modelPath = document.getElementById("src").value; which is currently line 294.

- Right below this line edit or and an If statment connecting the appropriate hotspot and annotation numbers to the correct model path:
	if(modelPath == "MODEL PATH"){
	      for (let i = (FIRST HOTSPOT NUMBER); i <= (LAST HOTSPOT NUMBER); i++) {
		document.getElementById("spot-" + i).setAttribute('class', "hotspot");
		document.getElementById("ant-" + i).setAttribute('class', "annotation");
	      }
	}

- The new hotspots should now load and unload with the proper model selection.
		
