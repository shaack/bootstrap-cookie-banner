# bootstrap-cookie-consent-settings

A modal dialog (cookie banner) and framework to handle the German and EU law (as written by EuGH, 1.10.2019 – C-673/17) 
about cookies in a website. Based on Bootstrap 4.

- [Demo page](https://shaack.com/projekte/bootstrap-cookie-consent-settings)
- [GitHub Repository](https://github.com/shaack/bootstrap-cookie-consent-settings)
- [npm package](https://www.npmjs.com/package/bootstrap-cookie-consent-settings)

## Usage

### Construct

Initialize the cookie consent framework with the constructor

```js
var cookieSettings = new BootstrapCookieConsent(props)
```

You may configure the framework with the `props` object. The default
configuration is

```js
this.props = {
    autoShowDialog: true, // disable autoShowModal on the privacy policy and legal notice pages, to make these pages readable
    lang: navigator.language, // the language, in which the modal is shown
    languages: ["en", "de"], // supported languages (in ./content/), defaults to first in array
    contentURL: "./content/", // this URL must contain the dialogs content in the needed languages
    cookieName: "cookie-consent-settings",  // the name of the cookie in which the configuration is stored as JSON
    cookieStorageDays: 365 // the duration the cookie configuration is stored on the client
}
```

### Show dialog again

On a new visit the dialog is shown automatically. 
For reconfiguration show the Dialog again with 

```js
cookieSettings.showDialog()
```

### Read the settings

Read all cookie settings with 

```js 
cookieSettings.getSettings()
```
It should return some JSON like

```json
{"necessary":true,"analysis":false}
```
or 
`undefined`, before the user has choosen his cookie options.

Read a specific cookie setting with 

```js
cookieSettings.getSettings('analysis')
```
for the `analysis` cookie settings. Also returns `undefined`, before the user has choosen 
his cookie options.