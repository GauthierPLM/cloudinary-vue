### Attributes

Refer to the base [Cloudinary JS SDK](https://github.com/cloudinary/cloudinary_js#configuration) for configuration options.

See the [Image transformation reference](https://cloudinary.com/documentation/image_transformation_reference) documentation for all the options accepted by the `CldPicture` and `CldTransformation` components.

```jsx
<cld-context cloudName="demo">
    <picture>
        <cld-source
            publicId="face_top"
            :media="{ screen: true, orientation: 'landscape', minHeight: 700 }"
            crop="thumb" aspectRatio="1.5" gravity="body"
        />
        <cld-source
            publicId="face_top"
            :media="{ screen: true, orientation: 'portrait', minWidth: 1200 }"
            crop="thumb" aspectRatio="0.66" gravity="body"
        />
        <cld-source
            publicId="face_top"
            :media="{ screen: true, orientation: 'landscape' }"
            crop="thumb" aspectRatio="2" gravity="face"
        />
        <cld-source
            publicId="face_top"
            :media="{ screen: true, orientation: 'portrait' }"
            crop="thumb" aspectRatio="0.5" gravity="face"
        />
        <img style="box-shadow: 0 5px 10px rgba(0,0,0,0.3)" />
    </picture>
</cld-context>
```