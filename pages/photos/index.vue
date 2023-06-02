<template>
  <div>
    <h2>Galeria przekazywanie parametrów przez route</h2>
    <div style="display: flex; flex-wrap: wrap">
      <div
        v-for="photo in photos"
        :key="photo.id"
        class="photo"
        style="padding: 5px"
      >
        <img
          :src="'https://picsum.photos/id/' + photo.id + '/200/300'"
          @click="openPhoto(photo)"
          style="width: 100%"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      photos: [
        {id: 1018,},{id: 1015,},{id: 1019,},{id: 1,},{id: 2,},{id: 3,},{id: 4,},
      ],
    };
  },
  methods: {
    openPhoto(photo) {
      this.$router.push({
        path: "/photos/" + photo.id,
      });
    },
  },
};
</script>
<style>
.photo {
  width: 100px;
  margin: 0;
}
</style>
