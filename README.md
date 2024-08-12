# Vue-Tags

A Flexible Vue.js 2 input Tag component where you can edit wathever you like related to HTML/CSS.


## Installation

1. Clone this repository
2. `npm i`
3. `npm run dev`
4. open http://localhost:3000 in your browser


## Getting Started

In your script entry point:

```html
<div id="app">

  <input-tags v-model="tags">
    <div class="tags-input"
            slot-scope="{tag,removeTag,inputEventHandlers,inputBindings }">
            <span v-for="tag in tags"
              class="tags-input-tag">
              <span>{{ tag }}</span>
              <button type="button" class="tags-input-remove"
                v-on:click="removeTag(tag)"
              >&times;
             </button>
            </span>
            <input
              class="tags-input-text"  placeholder="Add tag..."
              v-on="inputEventHandlers"
              v-bind="inputBindings"
            >
          </div>
   </input-tags>

</div>

window.Vue = require("vue");

import VueTags from "vue-tags";

//Vue.component("input-tags", VueTags); If you want a global Component

const app = new Vue({
  el: "#app",
  components: {
    VueTags
  },
  data: {
    tags: ['Laravel','Vuejs'],
  }
});
```

## Usage

Just add the tags as a v-model and follow the code above just don't change the vuejs attributes and the others is your choice do wathever you want with them.

### Props

By Default The tag is `added` when you click the `Enter Key` but you can customize it by adding `addKey` prop with KeyCode of your choice.
You can have it <a href="http://keycode.info/">here</a>.
For Example `188` for Comma `,`

```html
<div id="app">

  <input-tags v-model="tags" :addKey="188">
    <div class="tags-input"
            slot-scope="{tag,removeTag,inputEventHandlers,inputBindings }">
            <span v-for="tag in tags"
              class="tags-input-tag">
              <span>{{ tag }}</span>
              <button type="button" class="tags-input-remove"
                v-on:click="removeTag(tag)"
              >&times;
             </button>
            </span>
            <input
              class="tags-input-text"  placeholder="Add tag..."
              v-on="inputEventHandlers"
              v-bind="inputBindings"
            >
          </div>
   </input-tags>

</div>

const app = new Vue({
  el: "#app",
  components: {
    VueTags
  },
  data: {
    tags: ['Laravel','Vuejs'],
  }
});
```

By Default The tag is `deleted` when you click `delete Key` but you can customize it by adding `deleteKey` prop with KeyCode of your choice.
You can have it <a href="http://keycode.info/">here</a>.
For Example `13` for Comma `Enter`
Now When we click `Enter` we delete the tag
```html
<div id="app">

  <input-tags v-model="tags" :deleteKey="13">
    <div class="tags-input"
            slot-scope="{tag,removeTag,inputEventHandlers,inputBindings }">
            <span v-for="tag in tags"
              class="tags-input-tag">
              <span>{{ tag }}</span>
              <button type="button" class="tags-input-remove"
                v-on:click="removeTag(tag)"
              >&times;
             </button>
            </span>
            <input
              class="tags-input-text"  placeholder="Add tag..."
              v-on="inputEventHandlers"
              v-bind="inputBindings"
            >
          </div>
   </input-tags>

</div>

const app = new Vue({
  el: "#app",
  components: {
    VueTags
  },
  data: {
    tags: ['Laravel','Vuejs'],
  }
});
```

## Contributing

You are more than welcome to contribute to this repo with anything you think is useful. fixes are more than welcome.
