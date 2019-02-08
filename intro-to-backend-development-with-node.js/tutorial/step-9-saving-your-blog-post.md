---
description: 'Mini challenge #1'
---

# Step 9: Saving your blog post

{% hint style="info" %}
📣 Ok, so now it's time for a mini challenge. Steps 9 and 10 will require a little bit of your problem-solving skills. But don't worry, these mini challenges are 100% doable with the things you've learnt so far!

As always, chat with a mentor or collaborate with your neighbour if you need to.
{% endhint %}

Right now, your precious blog posts aren't being saved anywhere, which is a bit of a shame. Let's do something about that.

## JSON - the handy data format

You'll note that in the data folder there's a new file called `posts.json`.

JSON is a type of file for structuring data in a readable way. It is also a really popular format for sending data across the web.

JSON is a string representation of a Javascript object. JSON objects convert really easily to Javascript objects, and vice versa, with `JSON.parse()` and `JSON.stringify()`.

\(If you're not sure about JavaScript objects, have a chat with your mentor and your team.\)

If you look at `posts.json` will see there's already one blog post there. The format is:

{% code-tabs %}
{% code-tabs-item title="posts.json" %}
```javascript
{
    [timestamp]: [blog post message]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

We've used a timestamp as the key so that the blog posts are listed in chronological order. Also, it's a record of when the blog post was created.

## Writing to your hard drive

Anytime a blog post comes through to the server, we want to save the data on your computer's hard drive. To do this, we need to use a built-in Node module: `fs`, which stands for 'file-system'.

Built-in Node modules \(core Node modules\) are rather like the built-in Express middleware functions. Only difference is that where you need to have installed Express to use Express middleware functions, the core Node modules come automatically with Node itself.

To use `fs`, you'll need to require it at the top of your server file:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
var fs = require('fs');
```
{% endcode-tabs-item %}
{% endcode-tabs %}

The method we need to write to your hard drive is `fs.writeFile`.

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
fs.writeFile('location-of-your-file-goes-here', yourData, function (error) {
    // do something
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Let's look at this function more closely.

`fs.writeFile` takes 3 **arguments**:

* Argument 1: the location of the file you want to write to
* Argument 2: the data you want to write
* Argument 3: the callback function

The `'location-of-your-file-goes-here'` bit will be replaced with the actual path to the file you want to write to. If it doesn't exist, `fs.writeFile`cleverly creates one for you. But we already have `posts.json`, so not to worry.

## Reading from your hard drive

To read data that's already there, you would use `fs.readFile`. The way to use `fs.readFile` is very similar to `fs.writeFile`:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
fs.readFile('location-of-your-file-goes-here', function (error, file) {
    // do something
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

* Argument 1: the location of the file you want to write to
* Argument 2: the callback function

You'll notice that `fs.readFile`'s callback function takes a second argument, `file`. That argument would be the file you're reading.

Let's read the data from the `posts.json` file. Make sure you've `require`d the `fs` core Node module at the top of your server file somewhere.

Add this code to your server \(put it anywhere after the `require`s for now\):

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
fs.readFile(__dirname + '/data/posts.json', function (error, file) {
    console.log(file);
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
`__dirname` is a Node global object that gives you a path to current working directory. It's handy if we want to avoid writing the whole path out in full.
{% endhint %}

If you restart the server, you'll probably see something like this:

{% code-tabs %}
{% code-tabs-item title="Command line" %}
```bash
<Buffer 7b 0a 20 20 20 20 22 31 34 36 37 33 39 30 33 35 36 32 39 31 22 3a 20 22 54 68 69 73 20 69 73 20 6d 79 20 76 65 72 79 20 66 69 72 73 74 20 62 6c 6f 67 ... >
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This is actually the contents of your `posts.json` file, but in a format called a **buffer**. To make it a bit more human-readable, you can convert the file to a string, like this:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
console.log(file.toString());
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Converting from JSON to JavaScript object

`file` is in JSON format right now. If we want to access the blog post message inside `file`, we need to parse it from JSON back to a JavaScipt object.

Add this next bit of code to your `fs.readFile`'s callback function:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
var parsedFile = JSON.parse(file);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now `parsedFile` is a normal JavaScript object, and we can access the data inside it.

## Mini challenge

Ok, so we've talked about JSON and we've talked about reading and writing files. You now have the power to save new blog post data to your hard drive! Work with your neighbour and your mentor to see if you can figure the next steps out on your own.

Here's a breakdown of what you want to achieve:

1. When new blog post data comes through, read from `posts.json` to access its contents 
2. Add your new blog post data to the old ones. For each post, use a timestamp as the key, and the data as the value, just like the example in `posts.json` 
3. Write your new combined data back to the `posts.json` file

#### **Things to remember**

`fs.writeFile()` normally overwrites the target file you've given it. Chances are you don't want to lose all your old blog posts every time you get a new one, so think about how you can combine `fs.readFile()` and `fs.writeFile()`to prevent overwriting.

You will need to convert between JSON and a JavaScript object several times. `JSON.parse()` converts JSON to a JavaScript object. `JSON.stringify()` does the opposite \(JS object to JSON\). Use both of those.

Oh by the way, if you want to get the current timestamp, use the JavaScript `Date.now()` method.

**Good luck!  When you're done, move on to step 10.**

### [ ](https://github.com/node-girls/express-workshop/blob/master/step09.md)

