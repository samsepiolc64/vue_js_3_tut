<template>
  <div>
    <div>
      <p class="header">v-bind, czyli dynamiczne atrybuty, style i klasy</p>
      <p>Masks: {{ masks }}</p>
      <p v-if="masks > 3">dostepne</p>
      <p v-else-if="masks > 0 && masks <= 3">koncza sie</p>
      <p v-else>niedostepne</p>
      <button
        class="btn"
        @click="buyMask"
        :disabled="!masks"
        :class="{ 'btn--warning': masks <= 3 }"
      >
        Buy a mask
      </button>
    </div>
    <div>
      <img
        :src="images[currentImage]"
        :alt="`Image ${currentImage + 1}`"
        class="image"
      />
      <button
        class="btn"
        @click="changeImage"
        :disabled="currentImage >= images.length - 1"
      >
        go
      </button>
    </div>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";
export default {
  name: "MyComponent-vbind",
  setup() {
    const images = ref([
      "https://res.cloudinary.com/rebelwalls/image/upload/b_black,c_fill,f_auto,fl_progressive,h_533,q_auto,w_800/v1443017189/article/R13681_image1",
      "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTwwIbzHVQXt7BABMwVdg9BIVqyqPDlEtJIY4GtvchEy-5xn8DWSO9Qp85hWTnhV81F0AU&usqp=CAU",
      "https://static.posters.cz/image/1300/fototapety/above-the-clouds-sky-i77999.jpg",
      "https://www.almanac.com/sites/default/files/styles/opengraph/public/images/classifying-clouds.jpg?itok=glbJFEWA",
    ]);
    const currentImage = ref(0);

    const masks = ref(5);

    const styles = reactive({
      btn: {
        background: "#fceb76",
        color: "#fff",
      },
    });

    function buyMask() {
      masks.value--;
    }

    function changeImage() {
      currentImage.value++;
    }

    return {
      masks,
      buyMask,
      ...toRefs(styles),
      images,
      currentImage,
      changeImage,
    };
  },
};
</script>

<style lang="scss" scoped>
.header {
  font-size: 19px;
  color: aqua;
}

.btn {
  background: blueviolet;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 7px;
  cursor: pointer;
  &--warning {
    background: #ffc107;
    color: black;
  }
  &:disabled {
    cursor: default;
    background: #d3d3d3;
  }
}

.image {
  width: 200px;
}
</style>