# Step 1: Setting up your project

  
When creating a Node.js project, you will be installing a lot of different things along the way. If you want to share your project with others, you need to have a list of the things you installed, so that other people know what to install in order to run the project.

In Node.js, this 'list' file is called a `package.json`. The 'things you've installed' are referred to as [**dependencies**](../keywords.md#dependencies). Creating this file is the first step in setting up your Node.js project.

## Make a `package.json` file

Let's start by creating the `package.json` file. We can add things to it as the project grows. The `package.json` file is easy to create from the command line. Type the following command into your terminal to get started:

{% code-tabs %}
{% code-tabs-item title="Command line" %}
```bash
$ npm init
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
No need to include the dollar sign \($\) when typing this command.  It's there by convention when using the terminal.
{% endhint %}

This command will initialise a step-by-step process for creating the `package.json`. You should see something like this:

![](../../.gitbook/assets/image%20%284%29.png)

It will ask you the following questions:

**name**

npm suggests a default name for your project in brackets. If you want to give it your own name, just type it next to the brackets and press `Enter`.  Or if you're happy with the default name, just press `Enter`.

**version**

This is your first project, so it will be version 1.0.0! Nothing to change here, so just press `Enter`.

**description**

A description of your project. Write whatever you want and press `Enter`.

**entry point**

This file will be the starting point for your whole project.  Let's change this from `(index.js)` to `server.js`, as we will be building a server later on!

Type `server.js` and press `Enter`.

**test command**

Skip this one for now...press `Enter`.

**git repository**

This is where your project would live on GitHub. Press `Enter`.

**keywords**

\(Optional\) You can add keywords to help people find your project if they search for it.

**author**

It's your project, so write your name! You can use your GitHub name or your actual name.

**license**

You can add a license, but we'll skip this.

### Confirmation

You will see a confirmation of your `package.json`. If you're happy with it, press `Enter` to finalise its creation.

![](../../.gitbook/assets/image%20%285%29.png)

Great! You should now see a new file called `package.json` in your project's folder.

