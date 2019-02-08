# Individual Blog Posts

{% hint style="info" %}
This is an optional extension step, just for fun. It assumes you've already finished the tutorial.
{% endhint %}

We could make the CMS even better, by making it possible to retrieve and view individual blog posts.  Let's take a look at how we can do that.

### Step 1 - URL parameters

We don't want to have to write a handler for each URL in our application. Express's [URL parameters](https://expressjs.com/en/guide/routing.html#route-parameters) let us specify dynamic sections of the a URL - a space for a blog post ID or username, for example. You can think of them as function arguments being passed to your server.

Express's URL parameters use a `:` for dynamic parts of the URL:

* `/users/:userId` - matches URLs like `/users/123`, `/users/node-girls`
* `/users/:userId/posts/:postId` - matches URLs like `/users/node-girls/posts/node-is-best`

Let's add a handler for serving individual blog posts:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.get('/posts/:postId', function (req, res) {
    res.send('post id: ' + req.params.postId);
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

What do you think you'll see when you visit [http://localhost:3000/posts/abc123](http://localhost:3000/posts/abc123) in your browser?

### Step 2 - Reading from the file and sending the specific blog post

Just like with [`/create-post`](https://github.com/node-girls/express-workshop/blob/master/step08.md#reading-from-your-hard-drive), you need to read your JSON file. Try and send the post content back to the browser:`res.send(postContentHere)`

### Step 3 - Rendering a template

Right now we're just sending the plain text of your blog post, but you probably want to jazz up your post with some HTML and CSS. For this, we can use Express's built in templating system. You can use any template language you want \(like [pug/jade](https://pugjs.org/), [ejs](http://www.embeddedjs.com/), or [handlebars](http://handlebarsjs.com/)\), but we're going to use [mustache](https://mustache.github.io/) \(which is very similar to handlebars\) in this example.

Run `npm install --save mustache-express`, then check the documentation for [mustache-express](https://www.npmjs.com/package/mustache-express) and [Express's templating](http://expressjs.com/en/guide/using-template-engines.html). You'll need to create a template file in `views/post.mustache` like this:

{% code-tabs %}
{% code-tabs-item title="views/post.mustache" %}
```javascript
<!DOCTYPE html>
<html>
  <head>
    <title>Blog Post</title>
  </head>
  <body>
    <h1>yay blog post!</h1>
    <article>
      {{ post }}
    </article>
  </body>
</html>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

If you get stuck, check out the [example solution](https://github.com/node-girls/express-workshop-complete/tree/templating) :\)

### Even More Stretch Goals:

* Give your posts titles
* Add a post listing page
* Render posts as Markdown
* Yay!

