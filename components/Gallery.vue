<template>
  <div class="gallery">
    <div class="buttons">
      <div class="button left" @click="previousImage">
        <i><img src="https://cdn-icons-png.flaticon.com/512/2985/2985161.png" width="30px"/></i>
      </div>
      <div class="button right" @click="nextImage">
        <i><img src="https://cdn-icons-png.flaticon.com/512/2952/2952047.png" width="30px"/></i>
      </div>
    </div>
    <div class="main-image">
      <img :src="images[currentIndex]" @click="showModal = true" />
    </div>
    <div class="thumbnails">
      <div
        v-for="(image, index) in images"
        :key="index"
        :class="['thumbnail', { active: index === currentIndex }]"
        @click="changeImage(index)"
      >
        <img :src="image" />
      </div>
    </div>
    <div class="modal" v-if="showModal" @click="showModal = false">
      <div class="modal-content">
        <div class="description">
          <p>Hejka</p>
        </div>
        <img :src="images[currentIndex]" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      showModal: false,
      images: [
        "https://picsum.photos/500",
        "https://picsum.photos/501",
        "https://picsum.photos/502",
        "https://picsum.photos/503",
      ],
    };
  },
  methods: {
    previousImage() {
      this.currentIndex =
        this.currentIndex === 0
          ? this.images.length - 1
          : this.currentIndex - 1;
    },
    nextImage() {
      this.currentIndex =
        this.currentIndex === this.images.length - 1
          ? 0
          : this.currentIndex + 1;
    },
    changeImage(index) {
      this.currentIndex = index;
    },
  },
};
</script>

<style>
.gallery {
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.main-image {
  margin-bottom: 20px;
}

.description {
  background-color: #4F345A;
  color: #C9F299;
  padding: 5px 5px;
  margin: 5px 10px;
}

.main-image img {
  max-width: 100%;
  max-height: 500px;
  border: 5px solid #9CBFA7;
}

.thumbnails {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 20px;
}

.thumbnail {
  width: 80px;
  height: 80px;
  margin: 5px;
  cursor: pointer;
}

.thumbnail img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.thumbnail.active {
  border: 3px solid #C9F299;
}

.buttons {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.button {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 50px;
  height: 50px;
  margin: 0 10px;
  cursor: pointer;
  transition: transform 0.3s ease-in-out;
}

.button:hover {
  transform: scale(1.1);
}

.left i,
.right i {
  font-size: 1.5rem;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 999;
}

.modal-content {
  max-width: 90%;
  max-height: 90%;
}

.modal-content img {
  max-width: 100%;
  max-height: 100%;
}
</style>
