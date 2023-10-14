<template>
<title>Davlatlar</title>
  <div class="menu">
    <div class="container">
      <div class="menu_btn">
        <button v-for="(davlat, index) in davlatlar" :key="index" :class="{ active: activeBtn === index }"
          @click="activeBtn = index"> {{ davlat.name }}</button>
      </div>
      <!-- ----  end btn -->
      <div class="menu_item">
        <div class="item_left">
          <img :src="davlatlar[activeBtn].img" class="bayroq" alt="flag">
          <h2>Address</h2>
          <a href="#">{{ davlatlar[activeBtn]["address"].text }}</a>
          <h2>Phone</h2>
          <a href="#">{{ davlatlar[activeBtn]['phone'].text }} </a>
          <h2>Email</h2>
          <a href="#">{{ davlatlar[activeBtn]['email'].text }}</a>
          <h2>Web Site</h2>
          <a href="#">{{ davlatlar[activeBtn]['website'].text }}</a>
        </div>
        <!-- ------   item-left end -->
        <div class="right">
          <iframe :src="davlatlar[activeBtn].map" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      activeBtn: '0',
      davlatlar: [
        {
          name: "O'zbekiston",
          address: {
            text: "Toshkent Shahri",
            link: ''
          },
          phone: {
            text: '+998 (94) 150 29 28 ',
            link: ''
          },
          email: {
            text: "Amirxon@gmail.com",
            link: ''
          },
          website: {
            text: 'Amirxon.uz',
            link: ''
          },
          img: 'https://tfi.uz/photos/1/photos/flag-1024x512.jpg',
          map:'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d6009236.9501285525!2d62.24782286966444!3d42.657165105434174!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x38ae8b20a5d676b1%3A0xca0a6dad7e841e20!2z0KPQt9Cx0LXQutC40YHRgtCw0L0!5e0!3m2!1sru!2s!4v1697195628600!5m2!1sru!2s'
        },
        {
          name: "Xitoy",
          address: {
            text: "Xitoy",
            link: ''
          },
          phone: {
            text: '+998 (94) 150 29 28 ',
            link: ''
          },
          email: {
            text: "Amirxon@gmail.com",
            link: ''
          },
          website: {
            text: 'Amirxon.uz',
            link: ''
          },
          img: 'https://storage.kun.uz/source/uploads/2016mayiyun/fvtn1.jpg',
          map:'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d27123641.73901356!2d82.82978357183642!3d33.91562031443988!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31508e64e5c642c1%3A0x951daa7c349f366f!2z0JrQuNGC0LDQuQ!5e0!3m2!1sru!2s!4v1697196835308!5m2!1sru!2s'
        },
        {
          name: "Usa",
          address: {
            text: "Usa",
            link: ''
          },
          phone: {
            text: '+998 (94) 150 29 28 ',
            link: ''
          },
          email: {
            text: "Amirxon@gmail.com",
            link: ''
          },
          website: {
            text: 'Amirxon.uz',
            link: ''
          },
          img: 'https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/Flag_of_the_United_States_%28Pantone%29.svg/220px-Flag_of_the_United_States_%28Pantone%29.svg.png',
          map:'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d28294347.82343751!2d-137.0996365398369!3d30.039730056863092!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x54eab584e432360b%3A0x1c3bb99243deb742!2z0KHQvtC10LTQuNC90LXQvdC90YvQtSDQqNGC0LDRgtGLINCQ0LzQtdGA0LjQutC4!5e0!3m2!1sru!2s!4v1697197363229!5m2!1sru!2s'

        },
        {
          name: "Rassiya",
          address: {
            text: "Toshkent nimadir Rassiya",
            link: ''
          },
          phone: {
            text: '+998 (94) 150 29 28 ',
            link: ''
          },
          email: {
            text: "Amirxon@gmail.com",
            link: ''
          },
          website: {
            text: 'Amirxon.uz',
            link: ''
          },
          img: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARMAAAC3CAMAAAAGjUrGAAAAElBMVEX////VKx4AOaYAGJ4AOq3fKgABXnTtAAAA9UlEQVR4nO3QsQGAQAwAoejr/ivb50pbGIEZAAAAAAAAAAAAAAAAAAAAAH47bHOzOSkn5aSclJNyUk7KSTkpJ+WknJSTclJOykk5KSflpJyUk3JSTspJOSkn5aSclJNyUk7KSTkpJ+WknJSTclJOykk5KSflpJyUk3JSTspJOSkn5aSclJNyUk7KSTkpJzUP27xsc7E5KSflpJyUk3JSTspJOSkn5aSclJNyUk7KSTkpJ+WknJSTclJOykk5KSflpJyUk3JSTspJOSkn5aSclJNyUk7KSTkpJ+WknJSTclJOykk5KSflpJyUk3JSTspJOSkn5aQ+2jLMGymKnQ8AAAAASUVORK5CYII=',
          map:'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d59172283.80522189!2d32.11527164878419!3d25.149562585612593!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x453c569a896724fb%3A0x1409fdf86611f613!2z0KDQvtGB0YHQuNGP!5e0!3m2!1sru!2s!4v1697197590742!5m2!1sru!2s'

        }
      ]
    }
  }
}
</script>

<!-- Css -->

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: black;
}

.container {
  width: 1140px;
  margin: 0 auto;
  padding: 20px;
}

.menu_btn {
  display: flex;
  justify-content: space-between;
}

.menu_btn button {
  padding: 5px 20px;
  border: 1px solid white;
  background-color: transparent;
  color: white;
  border-radius: 30px;
  font-size: 20px;
  cursor: pointer;
}

.active {
  color: aqua !important;
  border-color: aqua !important;
}

/* ----  end btn */
.menu_item {
  margin-top: 100px;
  display: flex;
  justify-content: space-between;
}

.item_left {
  display: flex;
  flex-direction: column;
}

.item_left h2 {
  color: rgba(255, 255, 255, 0.479);
  margin: 25px 0 0 0;
  font-size: 20px;
}

.item_left a {
  color: white;
  text-decoration: none;
  font-size: 30px;
}

.item_left .bayroq {
  width: 300px;
  height: 150px;
}

/* -----  item_left */


/* .right {
  width: 500px;
  height: 500px;
  background-color: gray;
  border-radius: 20px;
} */
</style>
