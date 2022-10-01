<template>
  <div>
    <h2>Vue Js Google Maps with Multiple Markers Example</h2>

    <gmap-map :center="center" :zoom="15" style="width: 100%; height: 555px">
      <gmap-marker
        :key="index"
        v-for="(gmp, index) in locations"
        :position="gmp"
      ></gmap-marker>
      <GmapPolyline :path="paths"> </GmapPolyline>
    </gmap-map>
  </div>
</template>
 
<script>
export default {
  name: "userlocation-",
  data() {
    return {
      center: {
        lat: 0,
        lng: 0,
      },
      locations: [],
      currentLocation: null,
      paths: [
        {
          lat: 30.681445812915797,
          lng: 76.72593267775184,
          label: "SoftProdigy",
        },

        {
          lat: 32.103926752182645,
          lng: 76.53623763170091,
          label: "Home",
        },
      ],
    };
  },

  mounted() {
    this.setLocationLatLng();
  },

  methods: {
    setLocationLatLng() {
      navigator.geolocation.getCurrentPosition((geolocation) => {
        this.center = {
          lat: geolocation.coords.latitude,
          lng: geolocation.coords.longitude,
        };
      });

      this.locations = [
        {
          lat: 30.681445812915797,
          lng: 76.72593267775184,
          label: "SoftProdigy",
        },

        {
          lat: 32.103926752182645,
          lng: 76.53623763170091,
          label: "Home",
        },
      ];
    },
  },
};
</script>