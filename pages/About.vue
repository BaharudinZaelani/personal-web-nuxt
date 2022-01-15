<template>
  <div class="main">
    <div class="about" id="about">
      <div>
        <h1>About Me</h1>
        <p>
          Halo Baharudin Zaelani disini. Suka nonton anime silahkan, silahkan
          panggil anime lover sugan atau wibu terserah, gatau wibu
          kayakmana/anime lover kayak mana, tapi saya mendeskripsikan saya
          seorang anime lover karena kalo wibu itu udah tingkat akut seseorang
          yang mencintai budaya/segalanya tentang jepang. : padahal indonesia
          juga budayanya keren keren dan keren ..... :/, mungkin cuman
          ketinggalan teknologi aja.
        </p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.main {
  text-align: center;
}
.about {
  height: 100vh;
  display: grid;
  align-content: center;
}
.abou div {
  height: auto;
}
.about p {
  margin: auto;
  font-size: 1.4rem;
  width: calc(100vw - 230px);
}
@media screen and (max-width: 680px) {
  .about p {
    width: 100%;
  }
}
</style>
