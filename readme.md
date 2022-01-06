# React Build Info

While building a desktop web application using React, I realized that for support purposes I wanted the ability to display the app's build number (or even build date) in the application somewhere, and this module enables that.

## Installation

To install the module in your project, open a terminal window, navigate to a React project, and execute the following command:

```shell
npm install --save-dev react-build-info
```

## Operation

When you execute the module, it reads the local React project's `package.json` file, and, using the file's `version` property and the current date/time, creates a new file in the project at `src/buildInfo.ts` containing the following information:

```JavaScript
export const buildInfo = {
  buildVersion: "0.0.7",
  buildDate: 1611751534805,
}
```

To use the module in a React App, do something like the following:

```javascript
import React from 'react';

import buildInfo from './buildInfo';
import './App.css';
class App extends React.Component {

  componentDidMount() {
    console.log(`Build Number: ${buildInfo.buildVersion}`);
    const buildDate = new Date(buildInfo.buildDate);
    console.log(`Build Date: ${buildDate.toString()}`);
  }

  render() {
    return (
      <div>
        <header>
          <h1>Build Info</h1>
        </header>        
        <p>Bacon ipsum dolor amet chuck pork chop drumstick pork, rump bresaola swine shankle landjaeger tri-tip filet mignon ham tenderloin. Ham hock strip steak cow jerky pig biltong, drumstick salami beef ribs pastrami fatback spare ribs flank tail. Venison cupim alcatra tongue, drumstick sirloin beef salami cow pork loin brisket jowl. Bresaola flank pork chop ham chislic. Shoulder pastrami sausage, frankfurter meatloaf corned beef pig chicken. Shank chislic spare ribs, turducken fatback swine short ribs ball tip shankle brisket meatball shoulder frankfurter kevin pork chop.</p>
        
        <footer>By John M. Wargo</footer>
      </div>
    );
  }
}

export default App;
```

## Usage

Add this process to the existing `build` script entry, changing:

```text
"build": "react-scripts build",
```

to:

```text
"build": "npm version patch && react-build-info && react-scripts build",
```

The `npm version patch` part of the build step increments the patch version in the `package.json` file before calling `react-build-info`.

With this in place, when you execute `npm run build` to build a production version of the app, `npm` will update the version number in the project's `package.json` file, build an updated version of the buildinfo.js file, then generate the production build of the app.

***

You can find information on many different topics on my [personal blog](http://www.johnwargo.com). Learn about all of my publications at [John Wargo Books](http://www.johnwargobooks.com).

If you find this code useful and feel like thanking me for providing it, please consider <a href="https://www.buymeacoffee.com/johnwargo" target="_blank">Buying Me a Coffee</a>, or making a purchase from [my Amazon Wish List](https://amzn.com/w/1WI6AAUKPT5P9).
