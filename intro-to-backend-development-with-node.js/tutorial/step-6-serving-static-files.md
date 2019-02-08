# Step 6: Serving static files

So we know how to send back a simple message. But what if you want to send back a whole HTML page, or an image?

Things like HTML files, images etc are known as **static assets**. If you want your server to "serve" static assets back to the browser, you need to do something different than just using the `res.send()` method.

To be able to send any file from the server we need a special, built-in **middleware** function that comes with Express: `express.static()`. Read more about it [here](http://expressjs.com/en/starter/static-files.html).

Say we want to serve all the static assets in our `public` folder. The `express.static()` function will look like this:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.use(express.static("public"));
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Serve static files from your server

Delete all your `app.get` endpoint functions, and replace them with the line of code above. Restart your server, refresh your browser and see what happens! If you see a Node Girls CMS, then your static assets have been successfully served.

