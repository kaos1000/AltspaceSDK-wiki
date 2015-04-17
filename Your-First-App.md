This tutorial is a detailed walk-through of the Spinning Cube app from the SDK repo.

If you want a briefer step-by-step overview, see the [README].

### Step 1. Create your app HTML file

First clone or [download] the [AltspaceSDK Repo] from GitHub.

You can also using a GitHub GUI, command line shown here for brevity.
```
$ git clone git@github.com:AltspaceVR/AltspaceSDK.git
```
This will create the AltspaceSDK directory, with the following files and directories.
```
$ ls AltspaceSDK
src/
lib/
examples/
README.md
README.html
```
You could start building your app in this AltspaceSDK directory.  However, we recommend you **copy the SDK files into another directory** referenced by your app.  This will make your app more self-contained, and allow you to `git pull` changes from the AltspaceSDK repo without affecting your app.  Keep in mind this SDK is in BETA status and could change frequently, including non-backwards-compatible upgrades or discontinuing support for older versions.

For example, we create a MyFirstApp directory and copy SDK files as follows.
```
$ mkdir MyFirstApp
$ cp -r AltspaceSDK/src MyFirstApp/sdk
$ cp -r AltspaceSDK/lib MyFirstApp/lib
$ ls MyFirstApp/
lib/
sdk/
```
(If you use another directory structure, remember to adjust the paths used in your `<script>` tags below.)

Next, create an HTML file with script import tags pointing to the SDK files you copied above.  
```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>My First App</title>

    <script src="lib/three.min.js"></script>
    <script src="lib/OBJMTLLoader.js"></script>
    <script src="lib/MTLLoader.js"></script>
    <script src="sdk/AltOBJMTLLoader.js"></script>
    <script src="sdk/AltRenderer.js"></script>

</head>
<body>
</body>
</html>
```
You can name the above file index.html (if you will only have one app in this directory), MyFirstApp.html (which is what we use in this tutorial), or whatever you like. The SDK does not require any particular directory structure or file naming.

> Note to Experienced Web Developers: Following the convention used in the [Three.js Examples] directory, our sample app uses only one HTML file and limits use of JS libraries.  Feel free to put your Javascript into a separate file, or use additional libraries (require.js, underscore.js, etc). Yet keep in mind that Altspace Web Apps tend to follow game programming patterns (e.g. an animation loop that updates even when the user isn't providing any input), as opposed to MVC patterns used in web application frameworks.  Also, Altspace apps typically do little DOM manipulation often need only minimal HTML and CSS.  Instead, the bulk of the code is Javascript that manupulates the Three.js scene.

If your app will only run in Altspace, you do not need any CSS or HTML Body content.  Since this sample app will also work in a traditional web browser, we add info text that will appear at the top of the page, displaying the name of our app and a link back to this repo.  

Add the following CSS in your `<head>` section.
```
<style>
body {
	background-color: rgba(0, 0, 0, 0.5);
	margin: 0px;
	overflow: hidden;

	color: #FFFFFF;
	font-family: Monospace;
	font-size: 18px;
	text-align: center;
}
#info {
	position: absolute;
	top: 0px;
	width: 100%;
	padding: 10px;
}
</style>
```
The only line above related to Altspace is setting background-color as black with an alpha value of 0.5. This makes the web page appear semi-transparent when loaded in the Altspace personal browser.  

Add the following HTML in your `<body>` section.
```
<div id="info">
	<a href="http://github.com/AltspaceVR/AltspaceSDK" 
		target="_blank">AltspaceSDK</a> - My First App
</div>
```


[AltspaceSDK Repo]: https://github.com/AltspaceVR/AltspaceSDK
[README]: https://github.com/AltspaceVR/AltspaceSDK
[download]: https://github.com/AltspaceVR/AltspaceSDK/archive/master.zip
[Three.js Examples]: http://threejs.org/examples/