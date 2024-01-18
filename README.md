# H5P
[Demo] (https://camilo-mora.github.io/H5P/) on how to use H5P tools as stand alone.

H5P are interative tools that enhance and facilitate considerably learning concepts. While the tools are open source, they still require a server to host the app, in addition to wordpress capability. This prevents their use for fully autonomous pages, for instance like those hosted in Github.

There is a [code] (https://github.com/tunapanda/h5p-standalone) developed to make H5P stand alone, but it lacks instructions on how to use it. A good [video exist] (https://www.youtube.com/watch?v=GvQIljCP-m4), but it is out of date.

Here we provide a working example on how to turn H5P tools fully automonous in Github. Credit to the creators of the [code] (https://github.com/tunapanda/h5p-standalone) and to [Daisuke Horita] (https://github.com/CleanLake412) for working on the implementation.

Step 1. Copy all the files in this repository in your own.
Step 2. Take your H5P file and change the extension from .h5p to .rar

For instance: 08_experiment-8.h5p  should be renamed to 08_experiment-8.rar

Step 3. use any available siftware and unzip the rar file.

Step 4. Place all the full unzipped folder inside the H5P folder in the repository you createdd.

Step 5. In your webpage, add the following code in the position where you want the H5P tool.


```html
<div id="h5p-container-8"></div>
<script>
  (function() {
    let h5pContainer = document.getElementById("h5p-container-8"); // div tag ID
    let h5pJsonPath = 'H5P/08_experiment-8'; // H5P data directory path

    if (!document.getElementById('h5p-bundle-js')) {
      let script = document.createElement('script');
      script.id = 'h5p-bundle-js';
      script.src = 'libs/h5p/main.bundle.js';
      h5pContainer.parentNode.insertBefore(script, h5pContainer.nextSibling);
    }

    window.addEventListener("load", function() {
      const options = {
        h5pJsonPath: h5pJsonPath,
        frameJs: 'libs/h5p/frame.bundle.js',
        frameCss: 'libs/h5p/styles/h5p.css',
      }
      new H5PStandalone.H5P(h5pContainer, options);
    });
  }) ();
</script>



Step 6. In the code above replace the names of the H5P files for yours.. 

![Like](https://github.com/CleanLake412/H5P_Standalone/blob/master/howto/howto.png?raw=true)


Please pay attention to set variables h5pContainer, h5pJsonPath.
-  h5pContainer can be set as "h5p-container-" + h5p's frame number : h5p-container-8, h5p-container-9 ...
   This should be same as div tag's id attribute.
- h5pJsonPath should be set path of extracted H5P directory following upper instructions.

**All done !**



	


