 # Module 15: Packaging JavaScript for Production Deployment

# Lesson 2: Creating Separate Packages for Cross Browser Support

### Demonstration: Using Babel CLI to Compile JavaScript Code

#### Preparation Steps

Ensure that you have cloned the 20480C directory from GitHub. It contains the code segments for the labs and demos of this course. (**https://github.com/MicrosoftLearning/20480-Programming-in-HTML5-with-JavaScript-and-CSS3/tree/master/Allfiles**)

#### Demonstration Steps

#### Create New Project

1. Open Microsoft Visual Studio 2017.
2. In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.
3. In the left pane of the **New Project** dialog box, under **Installed**, expand the **Visual C#** node, and then click the **Web** node.
4. Click **ASP.NET Empty Web Application**.
5. In the **Name** box, type **babelDemo**.
6.	In the **Location** box, type **Allfiles\Mod15\DemoCode**, and then click **OK**.
7. In Visual Studio, on the **Project** menu, right-click **New Folder**.
8.  Name it **src**.
9.  In Visual Studio, in the **src** folder, right-click **Add New Item**.
10.  In the **Add New Item – babelDemo** dialog box, click **JavaScript File**.
11.  In the **Name** box, type **index.js**.
12.  Click **Add**.
13.  Add the following code:
```javascript
    let customer = { name: "Joann Chambers" };
    let message = `Hello ${customer.name}`;
```

#### Configure Babel on A new project

1.	In Visual Studio, on the **Project** menu, right-click **Add New Item**.
2.	In the **Add New Item – babelDemo** dialog box, click **npm Configuration File**.
3.	In the **Name** box, type **package.json**.
4.	Click **Add**.
5.  At the command prompt, navigate to the project folder.
6.  To install **babel-cli** and **babel-preset**, run the following command at the command prompt:
   ```bash
        npm install --save-dev babel-cli babel-preset-es2015
   ```
7.  Insert the following code to **package.json**:
   ```json
        "scripts": {
            "build": "babel --presets es2015 src -d dist"
        },
   ```
>**Note**: This code allows you to run **npm run build** without reference to **node_modules babel**. 

8.  At the command prompt, run the command:
```bash
        npm run build
```
>**Note**: The application creates the **dist** folder and the **new index** file according to the ECMAScript 2015 standards.

### Demonstration: Using Webpack and Babel to Build a JavaScript App

#### Preparation Steps 

Ensure that you have cloned the 20480C directory from GitHub. It contains the code segments for the labs and demos of this course. (**https://github.com/MicrosoftLearning/20480-Programming-in-HTML5-with-JavaScript-and-CSS3/tree/master/Allfiles**)

#### Demonstration Steps

#### Set Up Npm Configuration

1.	Open Visual Studio 2017.
2.	In Visual Studio, on the **File** menu, point to **Open**, and then click **File**.
3.	In the **Open File** dialog box, browse to the **Allfiles\Mod15\DemoCode\build-tutorial** folder, click **build-tutorial.sln**, and then click **Open**.
4.	In Visual Studio, on the **Project** menu, right-click **Add New Item**.
5.	In the **Add New Item – babelDemo** dialog box, click **npm Configuration File**.
6.	In the **Name** box, type **package.json**.
7.	Click **Add**.

#### Set Up Babel and Webpack

1.  In Visual Studio, on the **Project** menu, right-click **Add New Item**.
2.  In the **Add New Item – build-tutorial** dialog box, click **JavaScript File**.
3.  In the **Name** box, type **webpack.config.js**.
4.  Click **Add**.
5.  In the **webpack.config.js** file, configure **webpack** as follows:
   ```javascript
        var path = require('path');
        var webpack = require('webpack');
        module.exports = {
            entry: './scripts/app.js',
            output: {
                path: path.resolve(__dirname, 'build'),
                filename: 'app.bundle.js'
            },
            module: {
                rules: [
                    {
                        test: /\.js$/,
                        loader: 'babel-loader',
                        query: {
                            presets: ['es2015']
                        }
                    }
                ]
            },
            stats: {
                colors: true
            },
            devtool: 'source-map'
        };
   ```
6.  Open the **package.json** file and add a script named **webpack** that builds your application by using **webpack** and **Babel**.
   ```json
        "scripts": {
            "webpack": "webpack"
        },
   ```
7.  In build-tutorial, right-click **Add**, and then select **folder**.
8.  In the **Name** box, type **build**.
9.  Click **Add**.

#### Build and Run the App

1.  At the command prompt, run the following command:
   ```bash
        npm run webpack
   ```
2.  Open **index.html** and replace the script **src** value to the bundle file.
   ```html
        <script src="build/app.bundle.js"></script>
   ```
3.  Run the application.
4.  Open Microsoft Internet Explorer 10 and go to **http://localhost:51341/index.html**.
5.  Check whether the website runs in Internet Explorer 10 as it does in Microsoft Edge.

©2018 Microsoft Corporation. All rights reserved.

The text in this document is available under the  [Creative Commons Attribution 3.0 License](https://creativecommons.org/licenses/by/3.0/legalcode), additional terms may apply. All other content contained in this document (including, without limitation, trademarks, logos, images, etc.) are  **not**  included within the Creative Commons license grant. This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes.

This document is provided &quot;as-is.&quot; Information and views expressed in this document, including URL and other Internet Web site references, may change without notice. You bear the risk of using it. Some examples are for illustration only and are fictitious. No real association is intended or inferred. Microsoft makes no warranties, express or implied, with respect to the information provided here.
