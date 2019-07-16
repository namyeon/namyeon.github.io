
<!DOCTYPE html>
<html>
<header> 
	<h1> Slideshow </h1> 
	<p><span class="desc">Print designs </span> 
	</header> 	
	<div class="slideshow-class-goes-here">
    <figure>
        <img src="/logo.png" width="100%" />
        <figcaption>Caption goes here</figcaption> 
    </figure>
	</div>
	
	 
var makeBSS = function (el, options) {
    // a collection of all of the slideshows
    var $slideshows = document.querySelectorAll(el),
        
        // this slideshow instance 
        $slideshow = {},
        
        // the slideshow object we will use as prototype 
        Slideshow = {
            init: function (el, options) {
               /* ...
                  slideshow initialization stuff 
                  happens here */
            },
            showCurrent: function (i) {
               /* ...
                  show current slide and hide the rest
                  increment/decrement counter to keep track
                  of our place in the slideshow */
            },
            injectControls: function (el) {
               /* ...
                  add previous & next buttons 
                  to the slideshow */
            },
            addEventListeners: function (el) {
               /* ...
                  add event listeners to prev/next
                  buttons, and to left/right arrow keys
                  for keyboard navigation */    
            },
            autoCycle: function (el, speed, pauseOnHover) {
               /* ...
                  make slides auto-advance on a timer
                  and pause timer on hover */
            },
            addFullScreen: function(el){
               /* ...
                  add full screen toggle button */
            },
            addSwipe: function(el){
               /* ...
                  add touch/swipe functionality 
                  using hammerjs */
            },
            toggleFullScreen: function(el){
               /* ...
                  toggle full screen on/off
                  as button is clicked */ 
            } 
            
        }; // end Slideshow object 
        
    /* make instances of Slideshow as needed,
       the forEach makes it so that we can create multiple
       slideshows if $slideshows is a list of DOM elements */                     
    [].forEach.call($slideshows, function (el) {
        /* instantiate a new object 
           using Slideshow as its prototype */      
        $slideshow = Object.create(Slideshow);
        /* call the init method on the new object
           and pass in the options we've set */
        $slideshow.init(el, options);
    });
};
 
/* set up the options for the slideshow
   we're about to create */
var opts = {
    auto : {
        speed : 5000, 
        pauseOnHover : true
    },
    fullScreen : true, 
    swipe : true
};
 
/* call makeBSS, passing in the element(s)
   we want to make a slideshow, and the
   options we have set */
makeBSS('.demo1', opts);
 
 
 init: function (el, options) {
 
    /* to keep track of current slide */
    this.counter = 0; 
 
    /* current slideshow container element 
       create this as a property on the current object */
    this.el = el;     
 
    /* a collection of all of the individual slides */
    this.$items = el.querySelectorAll('figure'); 
 
    /* the total number of slides */
    this.numItems = this.$items.length; 
 
    /* if options object not passed in, then set to empty object [1] */
    options = options || {};  
 
    /* if options.auto object not passed in, then set to false */   
    options.auto = options.auto || false; 
 
    this.opts = {
        /* set the rest of the options, either to what 
           was passed in or to a default value. similar 
           to above only using the ternary operator [2] */
        auto: (typeof options.auto === "undefined") ? false : options.auto,
        speed: (typeof options.auto.speed === "undefined") ? 1500 : options.auto.speed,
        pauseOnHover: (typeof options.auto.pauseOnHover === "undefined") ? false : options.auto.pauseOnHover,
        fullScreen: (typeof options.fullScreen === "undefined") ? false : options.fullScreen,
        swipe: (typeof options.swipe === "undefined") ? false : options.swipe
    };
    
    /* add 'bss-show' class to first figure so that
       the first slide is visible when the slideshow loads */ 
    this.$items[0].classList.add('bss-show');  
    
    /* add the slideshow controls */
    this.injectControls(el);
    
    /* set up event listeners */
    this.addEventListeners(el);
 
    /* call methods for optional features */
    if (this.opts.auto) {
        this.autoCycle(this.el, this.opts.speed, this.opts.pauseOnHover);
    }
    if (this.opts.fullScreen) {
        this.addFullScreen(this.el);
    }
    if (this.opts.swipe) {
        this.addSwipe(this.el);
    }
}
 
 
 
 
</body>
</html>
