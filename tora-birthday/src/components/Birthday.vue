<template>
  <div class="birthday">
    <div class="birthday__label birthday__hint">
      Включи звук!
    </div>
    <div class="birthday__poem birthday__label">
      Be the best you can be,<br>
      Imagine what you can do,<br>
      Remember who you are,<br>
      There's nobody like you,<br>
      Honor your past,<br>
      Dwell on your heart,<br>
      All you need is love,<br>
      Your birthday is a start.<br>
    </div>
    <img src="../assets/Lovely-Happy-Birthday-Animated-GIF-image.gif">
    <p class="birthday__gift birthday__label">
      Вообщем, ничего лучше, чем оставить тебе свои наушники я и не придумал,<br>
      Теперь они по праву твои, если, конечно же, ты ими пользуешься =)
    </p>
  </div>
</template>

<script>
export default {
  name: 'Birthday',
  mounted() {
    document.addEventListener('scroll', this.handleScroll);
  },
  methods:{
    handleScroll(){

    }
  }
};
</script>

<style scoped>
.birthday {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;

}


.birthday__hint {
  font-size: 42px;
}

.birthday__label {
  width: 100vw;
  color: #db7d07;
  background-color: black;
}

.birthday__poem {
  padding-top: 100px;
  font-size: 36px;
  line-height: 36px;
}

.birthday__gift {
  font-size: 24px;
  padding-bottom: 200px;
}

img {
  width: 100%;
}

</style>