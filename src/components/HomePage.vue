<template>
  <div id="HomePage" class="splash container-lg">
    <div class="splash__outline row">
      <div class="splash__column col col--6">
        <h1>{{ item.hero_title }}</h1>
        <p>{{ item.hero_subtitle }}</p>
        <button>CRUSADE</button>
      </div>
      <div class="splash__column col col--6">
        <img :src="GamingController" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from '@/axios'

export default {
  name: 'HomePage',
  data () {
    return {
      GamingController: require('@/assets/svg/GamingController.svg'),
      item: {}
    }
  },
  mounted () {
    axios
      .get('pages/3/')
      .then(response => (this.item = response.data))
  }
}
</script>
<style>
.splash {
    height: 100%;
    padding: 50px 0px;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    background-color: #0c0a1c;
}

.splash__outline {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 5% 10%;
    background:
    linear-gradient(to right, var(--cyan-01) 4px, transparent 4px) 0 0,
    linear-gradient(to right, var(--cyan-01) 4px, transparent 4px) 0 100%,
    linear-gradient(to left, var(--cyan-01) 4px, transparent 4px) 100% 0,
    linear-gradient(to left, var(--cyan-01) 4px, transparent 4px) 100% 100%,
    linear-gradient(to bottom, var(--cyan-01) 4px, transparent 4px) 0 0,
    linear-gradient(to bottom, var(--cyan-01) 4px, transparent 4px) 100% 0,
    linear-gradient(to top, var(--cyan-01) 4px, transparent 4px) 0 100%,
    linear-gradient(to top, var(--cyan-01) 4px, transparent 4px) 100% 100%;
    background-repeat: no-repeat;
    background-size: 20px 20px;
    outline: 2px double rgba(45, 226, 230, 0.5);
    outline-offset: -3px;
    box-shadow:
    0px 0px 60px 10px rgba(45, 226, 230, 0.1),
    0px 0px 60px 10px rgba(121, 30, 148, 0.1)
    ;
}

.splash h1 {
    padding-bottom: 5%;
    font-size: 7rem;
    font-weight: 600;
    font-style: italic;
    color: #FFFF;
    text-shadow: 5px 0px 0px var(--pink-02),
    -5px 0px 0px var(--cyan-01),
    0px 0px 20px rgba(45, 226, 230, 0.8);
}

.splash p {
    color: var(--pink-03);
}
</style>
