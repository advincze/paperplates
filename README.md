#paperplates



## before running the application

#####bower

	$  bower install

or 

	$  bower update



## running the application

simple http servers

#####npm:

	$  npm install http-server -g
	$  http-server -p 8000
	
#####python2 : 
	
	$  python -m SimpleHTTPServer

## custom elements:


### &lt;super-drag&gt;&lt;/super-drag&gt;

**super-drag** extends core-drag-drop

super-drag emits drag events to its parentNode or Host (in a Polymer template, place it directly under the <template> tag)

Example:

```html
<polymer-element name="my-draggable-item" >
  <template>
    <super-drag></super-drag>
    <div>...</div>
    ...
  </template>
  <script>
  	Polymer({
		ready: function() {
			this.addEventListener('super-drag-start', function(e) {
				var dragInfo = e.detail;
				dragInfo.avatar.innerText = this.name;
			});
		}
	});
  </script>
</polymer-element>
```

available events:

* **super-drag-start**: dragging started
* **super-drag-drag**: dragging (coordinates, etc available)
* **super-drag-drop**: dragging ended 

e.detail = dragInfo from core-drag-drop



### &lt;super-drop&gt;&lt;/super-drop&gt;

super-drop registers for a dragged object by super-drag

Example:
```html
<polymer-element name="my-drop-target" >
  <template>
    <super-drop>
     ... <!-- elements can be dropped here -->

     <span>{{ message }}</span>
    </super-drop>
  </template>
  <script>
  	Polymer({
  		publish:{
  			message : ""
  		},
		ready: function(e) {
			this.addEventListener('super-drag-enter-my-draggable-item', function(e) {
				var draggableItem = e.detail;
				this.message = "an item is over me";
			});
			this.addEventListener('super-drag-leave', function(e) {
				this.message = "";
			});
			this.addEventListener('super-drop-my-draggable-item', function(e) {
				var draggableItem = e.detail;
				this.message = "an item was dropped on me";
			});			
		}
	});
  </script>
</polymer-element>
```
available events:

* **super-drag-enter**: an element was dragged onto an enclosed childNode
* **super-drag-enter-{custom-elem}**: a {custom-elem} element was dragged onto an enclosed childNode
* **super-drag-leave**: an element was dragged out of an enclosed childNode or dropped
* **super-drag-leave-{custom-elem}**: a {custom-elem} element was dragged out of an enclosed childNode or dropped
* **super-drop**: an element was dragged onto an enclosed childNode
* **super-drop-{custom-elem}**: a {custom-elem} element was dragged onto an enclosed childNode



##links


####webcomponents

[http://webcomponents.org/](http://webcomponents.org/)
[http://css-tricks.com/modular-future-web-components/](http://css-tricks.com/modular-future-web-components/)

####polymer:

[http://www.polymer-project.org/docs/start/creatingelements.html](http://www.polymer-project.org/docs/start/creatingelements.html)

[http://www.polymer-project.org/docs/elements/layout-elements.html](http://www.polymer-project.org/docs/elements/layout-elements.html)

[http://www.polymer-project.org/docs/polymer/layout-attrs.html](http://www.polymer-project.org/docs/polymer/layout-attrs.html)
