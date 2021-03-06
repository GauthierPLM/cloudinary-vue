### Attributes

Refer to the base [Cloudinary JS SDK](https://github.com/cloudinary/cloudinary_js#configuration) for configuration options.

See the [Image transformation reference](https://cloudinary.com/documentation/image_transformation_reference) documentation for all the options accepted by the `CldImage` and `CldTransformation` components.


### Events

Use `v-on:*.native` to listen to native DOM events. `CldImage` outputs an `img` element that does not have any events by default.

```vue
<template>
  <cld-image
    cloudName="demo"
    publicId="small_dinosaur"
    v-on:click.native="alert">
    <cld-transformation
      overlay="text:Arial_45:CLICK ME"
      background="red"
      radius="10"
      opacity="90"
      color="white" />
    <cld-transformation crop="scale" :height="100" />
  </cld-image>
</template>
<script>
export default {
  methods: {
    alert() {
      alert("I've used a native event listener to bind to a click event");
    }
  }
};
</script>
```

### Usage

```jsx
<cld-image cloudName="demo" publicId="small_dinosaur" />
```

General configuration options may be passed with a [CldContext](#cldcontext) containing component instead:

```jsx
<cld-context cloudName="demo">
  <cld-image publicId="small_dinosaur" />
</cld-context>
```

`CldImage` can also be given transformation data by setting manipulation attributes on the component itself or with a [CldTransformation](#cldtransformation) child component.

```jsx

// with the component itself:

<cld-image
    cloudName="demo"
    publicId="small_dinosaur"
    effect="blur:100"
    crop="scale"
    width="100"  />

// with a child CldTransformation component:

<cld-image 
  cloudName="demo" 
  publicId="small_dinosaur">
    <cld-transformation crop="scale" width="100" />
    <cld-transformation effect="blur:100" />
</cld-image>

```


### Responsive mode

Add the `responsive` property to have the image automatically adjust to the available width.

```jsx
<cld-image cloudName="demo" publicId="small_dinosaur" responsive>
  <cld-transformation effect="sharpen:300" />
</cld-image>
```

Responsive mode, but adjusting to height instead:

```jsx
<div class="explain" style="height: 75px; padding: 20px;">
  <cld-image cloudName="demo" publicId="small_dinosaur" responsive="height">
    <cld-transformation effect="sepia:95" />
  </cld-image>
</div>
```

### Lazy mode

Set the `lazy` property to only load the image when it needs to be displayed instead of when the page first loads.

Note: This feature is dependent on [IntersectionObserver](https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver) and will be disabled if it is not available.

```vue
<template>
  <cld-image
    cloudName="demo"
    publicId="small_dinosaur"
    lazy
    placeholder="color"
    @load.native="alert"
  >
    <cld-transformation crop="scale" :height="300" />
  </cld-image>
</template>

<script>
export default {
  methods: {
    alert() {
      console.log("lazy image loaded");
    }
  }
};
</script>
```
