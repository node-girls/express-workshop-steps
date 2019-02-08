# Step 7: Sending your blog post to your server

So far we have been requesting data from our server. But we can also _send_ data to the server to be stored somewhere.

## HTTP request methods

All requests use one of the HTTP methods. The main ones are: `GET`, `PUT`, `POST` and `DELETE`.

`app.get` deals with requests that use the `GET` HTTP method.

### The `POST` http request method

When sending data to the server, we use the `POST` http request method, instead of `GET`. To understand the difference, follow the "POST vs GET" link in the keywords section below.

Let's try `POST`ing some text to the server.

We're going to add a form to the `index.html` page, so that you can write your blogposts from there.

Open up the `index.html` file in your text editor. If you have a look, you should see this:

{% code-tabs %}
{% code-tabs-item title="index.html" %}
```markup
<div class="entry-container">
    <!--PASTE YOUR CODE HERE!! -->
</div>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**Replace the greyed-out comment with this code snippet:**

{% code-tabs %}
{% code-tabs-item title="index.html" %}
```markup
<h3>Create a blog post</h3>
<form action="/create-post" method="POST">
    <textarea name="blogpost" rows="10" cols="14"></textarea>
    <button type="submit">Send</button>
</form>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Let's look at this form a bit more closely.

* The form has a text area and a Send button.
* The `action` attribute is the endpoint form data will be sent to.
* The `name` attribute will be used later to reference the data.

When you hit Send, the form will send a `POST` request to the server, using whatever is in the `action` attribute as the endpoint. In our case it's `/create-post`.  So on our server, we will need to write some code to deal with requests that come in on the `POST /create-post` endpoint. 

## Receiving the blog post on the server

Data doesn't come through the server in one go; it flows to the server in a **stream**. Think of a stream as water flowing from a tap into a bucket.

If we were writing a pure Node server, we would have to think about how to collect the stream of data properly. But luckily for us, Express handles all of that stuff under the hood.

All you need to do is define a route to deal with requests that come through on the `/create-post` endpoint.

Let's remind ourselves of a `GET` route in Express:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.get('/my-lovely-endpoint', function (req, res) {
    res.send('Hello there!');
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

But this time we want to define a route to deal with a `POST` request. What do you think you would need to do differently? Experiment and see if you can define a route for the `/create-post` endpoint!

For now, make your `/create-post` handler do this: `console.log('/create-post')`.

{% hint style="info" %}
If you need a hint, ask a mentor or chat to your neighbour and see if you can work it out together!
{% endhint %}

If you manage to successfully handle requests on the  POST /create-post endpoint, you're ready to move on to step 8!

