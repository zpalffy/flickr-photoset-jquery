# flickr-photoset-jquery

A jQuery plugin for rendering [Flickr](https://www.flickr.com/) photosets.

Why?
====
Many flickr/jquery plugins exist already, why create another one?  I was looking for something extremely simple that didn't require anything specific in the way of DOM elements, or any specific CSS to get things to work.  I also liked the idea of specifying the "layout" with HTML templates.  This library does not require users to install any specific CSS, nor does it assume anything about the DOM layout surrounding the photoset element.

Example
=======
A simple example is included in the file named `example.html`.  The example takes a [Flickr API Key](https://www.flickr.com/services/api/keys/) and photoset id as parameters and displays the photoset on the page.

Usage
=====
To use the plugin, you will first need to acquire a unique [Flickr API Key](https://www.flickr.com/services/api/keys/).  The API Key will be used on all calls to gather photos from the set and is required by the Flickr json api.

Next, download the script file and include it after jQuery has been included on the page, e.g.

``` html
<script src="/path/to/jquery.js"></script>
<script src="flickr-photoset-jquery-<version>.js"></script>
```

Then either add a container element or create one dynamically that will contain the photos from the photoset:

``` html
<div id="photos"></div>
```

To fill the contents of the container, call the `flickrPhotoset` method with your Flickr API Key and the photoset id of the photoset to display: 

``` javascript
$('#photos').flickrPhotoset('<apiKey>', '<photosetId>')
```

Options
=======
A number of options may be passed in to the `flickrPhotoset` call as the third parameter:

Name | Description | Default
---- | ----------- | -------
before | HTML template placed before the jQuery element reference.  **{{url}}** may be be used to refer to the photoset url, while **{{title}}** may be used to insert the photoset name. | `<h3><a href="{{url}}">{{title}}</a></h3>`
template | HTML template used for each photo in the set.  **{{link}}** may be used to refer to the link to the photo, **{{img}}** refers to the image itself, **{{title}}** is the image title.  Also notice the '_q' used in the image source - this is the size of the image to display and is described in more detail in Flickr's documentation for [Photo Source URLs](https://www.flickr.com/services/api/misc.urls.html) | `<a href="{{link}}" title="{{title}}"><img src="{{img}}_q.jpg" alt="{{title}}"/></a>`
loading | A jQuery element that is displayed while the photoset is loading. | none

Events
======
The jQuery element will fire an event named `photoset` when the photoset has been successfully loaded.  Example usage:

``` javascript
$('#photos').flickrPhotoset('<apiKey>', '<photosetId>').bind('photoset', function(evt, photos) {
    console.dir(photos); // lists the photoset json structure in the console
});
```

Of course the listener does not need to be bound directly to the element itself, but could be bound to any parent element in the DOM - just the same as all jQuery events.

History
=======
* **1.0** Initial commit
