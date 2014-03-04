# Getting Started with Flickr

1. Need a Flickr account!

2. Get your API Key: http://www.flickr.com/services/apps/create/

3. Flickr API Docs: http://www.flickr.com/services/developer/

4. Open HelloWorldFlickr.html

## What the $%&^?

###The URL

The most important thing to get your head around is how you access the Flickr API using a special URL. You construct this URL to 'ask' for the data you are after.  The first part of this URL is
    
```
http://api.flickr.com/services/rest/
```

You then add things to specify what you are after. The first thing you add is the method
    
```
http://api.flickr.com/services/rest/?method=flickr.photos.search
```

You then add the arguments and the format you need, which have an & sign between each one

```    
http://api.flickr.com/services/rest/?method=flickr.photos.search&api_key=1c9f777eb7446f34a7261dc1a54be4b2&tags=kitten&format=json&jsoncallback=?
```

The `api_key` is the code you got earlier. You can construct this URL manually by looking at the documentation for your chosen method but this is a bit fiddly.

#### URL Wizard

Fortunately, Flickr offers a link to a handy wizard (called API Explorer) at the bottom of each ‘method’ page. 

NOTE FOR TEACHERS: By default the URL generated by the wizard has ‘nojsoncallback=1’ at the end. As we need to push the results into a function, in our case the end should be ‘nojsoncallback=?’

So, to construct your URL that calls the Flickr API, you need to:

- Go to the Flickr API Documentation homepage and select the method that you want to use.
- Then on the `method` page, take a closer look at the description and the details to make sure this is the one for you. Then scroll right down to the bottom of the page and click on the API explorer link.
- On the API explorer page, fill in the relevant information about the arguments, and then scroll down. Select the JSON output. And, select `Do not sign call?` as we are looking at public data.  Then click the Call Method button.
- Take a look at the bottom of the screen now. You should see it’s presented you with the results of your query. And, right at the end, there’s the URL you need!
- If you copy this URL into your browser, you’ll actually see the result of the query. They are often a bit hard to read, but if you copy the results into the JSON Formatter (http://jsonformatter.curiousconcept.com/) then all will be revealed. 
- As mentioned above, before using this URL to call Flickr from within your own web pages, alter the end to  `nojsoncallback=?`, and remember to replace the `api_key` argument with your own key.

### Capture the Results

Once you've constructed your URL that calls the Flickr API we need a way of capturing the results. We do this using the $.getJSON jQuery method. The $.getJSON method reads in data that's in the JSON format and calls a function (in this case `displayImages2`), which processes the data in some way (in this case displaying the images on a web page).

### Wait - What Exactly is JSON?

While we are on the subject of JSON, it’s worth pointing out that JSON is just a way of formatting or structuring information so a computer can read it. If you look at the JSON output, you can start to see how the code is accessing each bit of the data. 

So, for example, data.photos.photo is directing the javaScript into the photo array in the JSON where most of the information is stored. Then, for example, var photoID = item.id; is accessing the id element for each photo.

## Exercises

- Change the URL in the example to find photos in New York City.
- Change the URL in the example to find photos of the Statue of Liberty.
- Change the HTML code to put the photos in a grid.