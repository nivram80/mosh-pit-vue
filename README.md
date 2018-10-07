# Install
`npm i mosh-pit-vue`

# Config
Add a `vue.config.js` file to the root directory of your application if it doesn't already exist.

Add the following code to the `vue.config.js` file:
```$xslt
const path = require('path')

module.exports = {
  pluginOptions: {
    'style-resources-loader': {
      preProcessor: 'scss',
      patterns: [
        path.resolve(__dirname, 'src/assets/config.scss'),
        path.resolve(__dirname, 'src/assets/mixin.scss')
      ]
    }
  }
}
```

Add the config.scss and mixin.scss files found in the mosh-pit-vue src/assets directory to your project's src/assets directory.  

If you decide to use a different path for your project, make sure you adjust the `path.resolve...` paths in the `vue.config.js` file.


## Customize the global styles of your project
Now you can change the variables in your project's `config.scss` file to your liking.


# Components Available To Use So Far
Add whatever available mosh-pit components to your component:
```
  export default {
    ... 
    components: {
      MoshButton,
      MoshSelect,
      // etc...
    },
    ...
```
### Buttons
```
  <MoshButton 
    :label="'Submit'"
    :type="'primary'"
    @buttonClick="submitFunction"
  />
```

Right now there are two types of buttons, `primary` and `secondary`.

### Selects
```
  <MoshSelect
    :label="'Best Royals Player'"
    :placeholder="'Choose...'"
    :options="players"
    :model="bestPlayer"
    @setOption="setPlayer"
  />
```
### Text Inputs
```
  <MoshTextInput
    :label="'First Name'"
    :placeholder="'Optional'"
    :model="firstName"
    @setValue="setFirstName"
  />
```
### Textareas
```
  <MoshTextarea
    :label="'Comments'"
    :placeholder="'Optional'"
    :model="comments"
    @setValue="setComments"
  />
```

# Disable Components
All components accept the optional `isDisabled` attribute that will add an opacity and disable pointer events on the component:
```
  <MoshButton 
    :label="'Submit'"
    :isDisabled="true" // defaults to false
    @buttonClick="submitFunction"
  />
```