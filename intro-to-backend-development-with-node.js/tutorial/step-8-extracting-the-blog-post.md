# Step 8: Extracting the blog post

So now we have a handler for `/create-post`.  Next step is to actually find our blog post.

The contents of your blog post is hidden in your `req` object somewhere. Normally you would extract it using `req.body`. Try to console.log `req.body` now.

Getting `undefined`? Not to worry, that's normal. When data has been `POST`ed to the server as `FormData`, we need to do things slightly differently to access the data that's come through in the request.

We need another middleware function. Something that can get extract the contents out of the special `FormData` object. For this we will use `express-formidable`. `express-formidable` is another Express middleware. It will extract the form data from the request and make it available to you when you do `req.fields`.

This time though, `express-formidable` is not built-in, we need to explicitly install it.

## **Installing `express-formidable`**

Go to your terminal and install express-formidable:

{% code title="Command line" %}
```bash
npm install express-formidable --save
```
{% endcode %}

Next, you need to `require` the `express-formidable` library so you can use it in your code. You can't use dashes in JavaScript variable names, so just call it `var formidable`.  Require it somewhere near the top of `server.js`, near the other `require`d code.

{% code title="server.js" %}
```javascript
var formidable = require('express-formidable');
```
{% endcode %}

Now somewhere between your `require`s and your `/create-post` endpoint, add this:

{% code title="server.js" %}
```javascript
// require stuff above

app.use(formidable());

// endpoint stuff below
```
{% endcode %}

Finally, inside your /create-post function, add this:

{% code title="server.js" %}
```javascript
console.log(req.fields);
```
{% endcode %}

Refresh your server and have another go at writing a blog post.

You should now see an object in the console. The key should be `blogpost`, just like the name attribute in the form on the HTML page. The value of `blogpost` will be your message!

