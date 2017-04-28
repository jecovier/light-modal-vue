# LIGHTMODAL
Light modal component for Vue, based on the Modal Component Example and added some features like:
- close on outside click
- slot support
- some animations

## ✔ Getting started
Please refer to [Official Documentation](https://bootstrap-vue.github.io) for setup guide, examples and documentation.

Get the package:
```bash
npm install light-modal-vue
```

Register LightModal in your app entrypoint:
```js
import Vue from 'vue'
import LightModal from 'light-modal-vue';

Vue.component('light-modal', LightModal);
```

## Integrate Animate.css
Get Animate.css:
```bash
npm install animate.css
```
Import animate.css in your app
```js
import 'animate.css/animate.min.css';
```
use it with LightModal
```html
<modal
	v-show = "show"
	title  = "Title"
	intro  = "bounceIn"
	outro  = "bounceOut"
	@close = "close">
</modal>
```


## License
MIT



#### Status
This project is in an early stage of development. Any contribution is welcome :D
