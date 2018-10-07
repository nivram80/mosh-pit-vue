# Install
`npm i mosh-pit-vue`

# Config
Add a `vue.config.js` file to the root directory of your application if it doesn't already exist.

Add the following code to the vue.config.js file:
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

Add the config.scss and mixin.scss files found in the src/assets directory to your project's src/assets directory.


## Customize the global styles of your project
Change the variables in the `config.scss` file now in your project to your liking.


# Components Available To Use So Far
Add whatever available mosh-pit components to your component:
```
  export default {
    ... 
    components: {
      MoshButton,
      MoshSelect
    },
    ...
```
- Buttons
  ```
    <MoshButton 
      :label="'Submit'" 
      @buttonClick="submitFunction"
    />
  ```
- Selects
  ```
    <MoshSelect
      :label="'Best Royals Player'"
      :placeholder="'Choose...'"
      :options="players"
      :model="bestPlayer"
      @setOption="setPlayer"
    />
  ```