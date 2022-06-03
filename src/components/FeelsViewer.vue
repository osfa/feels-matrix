<template>
  <div style="width: 100%; height: 100%" id="viewer-image" ref="image"></div>
</template>
<script>
import OpenSeadragon from "openseadragon";
window.OpenSeadragon = OpenSeadragon;
export default {
  name: "FeelsViewer",
  data() {
    return {
      viewer: null,
    };
  },
  mounted() {
    this.initViewer();
  },
  methods: {
    initViewer() {
      console.log("init Viewer");

      var ts = {
        Image: {
          xmlns: "http://schemas.microsoft.com/deepzoom/2008",
          Url: "/default-dzi-woj1.1_files/", //'/dzsave-test-wish_files/',
          Format: "jpeg",
          Overlap: "1",
          TileSize: "256",
          ServerFormat: "Default",
          Size: {
            Height: "58880",
            Width: "58880",
          },
        },
      };

      this.viewer = OpenSeadragon({
        id: "viewer-image",
        maxImageCacheCount: 5000,
        tileSources: ts,
        // imageSmoothingEnabled???
        showNavigator: false,
        showRotationControl: false,
        animationTime: 1, //5,
        blendTime: 0.1, //0.5,
        showNavigationControl: false,
        // maxZoomPixelRatio: 2, // default 1.1 The maximum ratio to allow a zoom-in to affect the highest level pixel ratio.
        // This can be set to Infinity to allow 'infinite' zooming into the image
        minZoomLevel: 1,
        maxZoomLevel: 24,
        visibilityRatio: 1, // ?
        //constrainDuringPan: true, // prevents bounceback anim
        autoResize: true, // viewport resize adapt
        zoomPerScroll: 2,
        defaultZoomLevel: 6, // 2 if mobile, calc based on width?
        // minZoomLevel: 1, // 2 if mobile calc based on with?
        // wrapHorizontal: true,
        // wrapVertical: true,
      });

      this.viewer.addHandler("open", () => {
        this.viewer.addHandler("zoom", () => {
          console.log("zoom", this.viewer.viewport.getZoom());
          // howl trigger...
        });
      });
      // this.viewer.initializeAnnotations()
      /* OpenSeadragon({
        animationTime: 0.4,
        id: "viewer-image",
        tileSources: {
          type: "image",
          url: "https://picsum.photos/id/237/200/300"
        },
        visibilityRatio: 0.2
      });*/
    },
  },
};
</script>
