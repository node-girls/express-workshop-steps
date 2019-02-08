# Step 2: Installing Express

Before we write any code, you'll need to install the Express library. We're going to use the [**Node Package Manager \(npm\)**](https://www.npmjs.com/)to download it using the **`npm install`** command.

NPM is the place to go to download other Node code written by other people. There are thousands of open-source, 3rd-party Node modules \(also known as "packages"\) by other people that you can download and use in your own projects.

As we install Express, we'll need to update the `package.json` to add Express as a dependency. We do this so that other people working on the project will know to install Express before running any of the code. This can be done by adding **`--save`** to the end of your command.

**Run the following command in your terminal:**  


{% code-tabs %}
{% code-tabs-item title="Command line" %}
```bash
$ npm install express --save
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Express should now be installed. Check your `package.json` file to make sure it has been added as a dependency. It will look something like this:

![](../../.gitbook/assets/image%20%288%29.png)

