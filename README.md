# vuetify-upload-btn
Simple component to handle file selection for upload.

## Installation

Copy ```FileUploadComponent.vue``` to part of your project and require/import if using bundler.

Tested to work with Vue 2.5.x and Vuetify 1.0.3 

## How to use

In your view or component import file:

```
import VFileUpload from './FileUploadComponent';
```

add it to components section:

```  export default {
    components: {
      VFileUpload,
```

Use props to customize the field:

```
<v-file-upload
        label="Photo"
        accept="image/jpeg"
        v-model="photo"
        :error-messages="errors.collect('photo')"
        required></v-file-upload>
```

It will act as any other field and store the file information on the model specified(here `photo`).

## Screenshot
![Screenshot](https://raw.githubusercontent.com/eAdnan007/vuetify-upload-btn/master/screenshot.png)
 
## License 
Released under [MIT](https://opensource.org/licenses/MIT) license.
