# Step 5: Routing

At the moment our server only does one thing. When it receives a request from the `/` endpoint, it sends back the same response: "Yay Node Girls!".

Want to check? Try typing [http://localhost:3000/nodegirls](http://localhost:3000/nodegirls) and see what happens.

However by making use of endpoints, we can make the server send different responses for different requests. This concept is called **routing**.

## What is an endpoint?

An endpoint is the part of the URL which comes after `/`. For example: `/chocolate` is the "chocolate" endpoint. It's the URL to which you send a request.

### 1. Create your own endpoints and send different responses

We're going to try sending different responses at different endpoints. Remember the `app.get()` method? To set up routing in your server, we just need to repeat this method with different endpoints.

For example:

{% code-tabs %}
{% code-tabs-item title="server.js" %}
```javascript
app.get("/", function (req, res) {
    res.send("Hello World!");
});

app.get("/chocolate", function (req, res) {
    res.send("Mm chocolate :O");
});
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
_Challenge:_ Add some code so that your server sends one message when the endpoint is `/node` and another one when it's `/girls`.
{% endhint %}

