# flickr-photoset-jquery

A jQuery plugin for rendering [Flickr](https://www.flickr.com/) photosets.

Why?
====

Example
=======
A simple example is included in this project named `example.html`.  The example takes a Flickr API Key and photoset id as parameters and displays the photoset on the page.

Usage
=====
To use the plugin, you will first need to acquire a unique Flickr API Key.  The API Key will be used on all calls to gather photos from the set and is required by the Flickr json api.

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

History
=======
* **1.0** Initial commit
