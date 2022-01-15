<template>
  <div>
    <div class="main">
      <div class="new">
        <div class="one mobile">
          <div>
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-code-slash"
              viewBox="0 0 16 16"
            >
              <path
                d="M10.478 1.647a.5.5 0 1 0-.956-.294l-4 13a.5.5 0 0 0 .956.294l4-13zM4.854 4.146a.5.5 0 0 1 0 .708L1.707 8l3.147 3.146a.5.5 0 0 1-.708.708l-3.5-3.5a.5.5 0 0 1 0-.708l3.5-3.5a.5.5 0 0 1 .708 0zm6.292 0a.5.5 0 0 0 0 .708L14.293 8l-3.147 3.146a.5.5 0 0 0 .708.708l3.5-3.5a.5.5 0 0 0 0-.708l-3.5-3.5a.5.5 0 0 0-.708 0z"
              />
            </svg>
          </div>
          <h3>
            Free and Pay <br />
            Source code
          </h3>
        </div>
        <div class="mid mobile" id="website"></div>
        <div class="three"></div>
      </div>
      <section class="product">
        <div>
          <a class="text-hover" href="show">
            <h3>SHOW ME EVERYTHING</h3>

            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="16"
              height="16"
              fill="currentColor"
              class="bi bi-arrow-right"
              viewBox="0 0 16 16"
            >
              <path
                fill-rule="evenodd"
                d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8z"
              />
            </svg>
          </a>

          <div id="container" v-for="product in product" :key="product">
            <div class="product-details">
              <h1>{{ product.name }}</h1>
              <span class="hint-star star">
                <i class="fa fa-star" aria-hidden="true"></i>
                <i class="fa fa-star" aria-hidden="true"></i>
                <i class="fa fa-star" aria-hidden="true"></i>
                <i class="fa fa-star" aria-hidden="true"></i>
                <i class="fa fa-star-o" aria-hidden="true"></i>
              </span>

              <p class="information">
                {{ product.description }}
              </p>

              <div class="control">
                <button class="btn">
                  <a :href="product.demo" target="_blank">
                    <span class="price">-</span>
                    <span class="shopping-cart">
                      <!-- <svg
                      xmlns="http://www.w3.org/2000/svg"
                      width="16"
                      height="16"
                      fill="currentColor"
                      class="bi bi-cart"
                      viewBox="0 0 16 16"
                    >
                      <path
                        d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .491.592l-1.5 8A.5.5 0 0 1 13 12H4a.5.5 0 0 1-.491-.408L2.01 3.607 1.61 2H.5a.5.5 0 0 1-.5-.5zM3.102 4l1.313 7h8.17l1.313-7H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"
                      />
                    </svg> -->
                    </span>
                    <span class="buy">DEMO</span>
                  </a>
                </button>
              </div>
            </div>
            <div class="product-image">
              <img :src="product.image.desktop" />

              <div class="info">
                <h2>Detail</h2>
                <!-- {{ product }} -->
                <ul>
                  <li><strong>Download : </strong> {{ product.download }}</li>
                  <li><strong>View : </strong> {{ product.view }}</li>
                  <li><strong>Upload At: </strong> {{ product.created_at }}</li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>

    <section class="more" id="project">
      <div class="main">
        <div class="search-content">
          <input type="text" placeholder="SEARCH" />
          <div class="cari">Cari sesuai keinginan anda</div>
          <div class="content">
            <div
              class="blog-card"
              v-for="(item, index) in lProduct"
              :key="index"
            >
              <div class="meta">
                <div
                  class="photo"
                  :style="{
                    backgroundImage: 'url(' + item.image.desktop + ')',
                  }"
                ></div>
              </div>
              <div class="description">
                <h1>{{ item.name }}</h1>
                <h2>-</h2>
                <p>
                  {{ item.description }}
                </p>
                <p class="read-more">
                  <a href="#">Read More</a>
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="side-content">
          <div class="ads">
            <img
              src="https://i.ibb.co/9vzbs54/Putih-dengan-Biru-Air-Sapuan-Kuas-Personal-Logo.png"
              style=""
            />
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {
      product: {},
      lProduct: {},
      // img: "background-image: url(https://storage.googleapis.com/chydlx/codepen/blog-cards/image-1.jpg);",
    };
  },
  mounted() {
    this.getProduct("Simple");
    this.getlProduct();
    // console.log(products);
  },
  methods: {
    async getProduct(key) {
      // const token = "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJjcmVhdGVkIjoyMDIxfQ._sTK1vIqVnoNdx1uIVRtVWq6XKJAhQuCjPsvSxZsItU";

      // const res = await this.$axios.get(
      //   "/project?token=" + token + "&search=category&key=web"
      // );

      const res = await this.$axios.get(key);
      this.product = res.data;
      // console.log(res.data);
    },
    async getlProduct() {
      const res = await this.$axios.get();
      this.lProduct = res.data;
      console.log(res);
    },
  },
};
</script>
<style scoped>
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}
.ads {
  position: -webkit-sticky; /* Safari */
  position: sticky;
  top: 0;
  height: 320px;
  background-color: rgb(255, 255, 255);
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}
.content {
  margin-top: 12px;
  position: relative;
  z-index: 999;
}
.more-content {
  width: 90%;
  margin: auto;
}
.cari {
  position: absolute;
  top: 0;
  bottom: 17px;
  right: 0;
  background-color: rgb(247 234 201);
  padding: 8px;
  opacity: 0;
}
.search-content:hover .cari {
  opacity: 1;
}
.search-content {
  position: relative;
}
.more .main {
  grid-gap: 2rem;
  display: grid;
  grid-template-columns: 2fr 1fr;
}
.search-content input:focus {
  width: 80%;
  border: none !important;
  border-radius: 0;
  outline: none;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}
.search-content input {
  height: 18px;
  border: none;
  padding: 12px;
  width: 50%;
  display: grid;
}
.shadow {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
}
.more {
  background-color: #f3ddaa4b;
  margin-top: 60px;
}
.contact {
  height: 10vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.contact #container {
  height: auto;
  background-color: #118847;
  color: #e9ad85;
}
.product {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
a {
  text-decoration: none;
  color: black;
}
a:hover {
  color: black;
}
.three {
  display: flex;
  justify-content: end;
}
.three h3 {
  display: inline;
}
.bi-arrow-right {
  padding-top: 5px;
}
.one {
  display: grid;
  grid-template-columns: 1fr 5fr;
}
.one div {
  display: flex;
  justify-items: center;
  align-items: center;
  margin: auto;
}
h3 {
  display: inline;
}
.bi-code-slash {
  transform: scale(2);
  padding-right: 12px;
}
.new {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
}
.text-hover::before {
  transform: scaleX(0);
  transform-origin: bottom right;
}

.text-hover:hover::before {
  transform: scaleX(1);
  transform-origin: bottom left;
}

.text-hover::before {
  content: " ";
  display: block;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  inset: 0 0 0 0;
  background: #e2c275;
  z-index: -1;
  transition: transform 0.3s ease;
}

.text-hover {
  position: relative;
  font-size: 1rem;
}

/* card */

#container {
  text-align: center;
  overflow: hidden;
  height: 350px;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  width: 90vw;
}

.product-details {
  position: relative;
  text-align: left;
  overflow: hidden;
  padding: 30px;
  height: 100%;
  float: left;
  width: 40%;
}

#container .product-details h1 {
  /* font-family: "Bebas Neue", cursive; */
  display: inline-block;
  position: relative;
  font-size: 30px;
  color: #344055;
  margin: 0;
}

#container .product-details h1:before {
  position: absolute;
  content: "";
  right: 0%;
  top: 0%;
  transform: translate(25px, -15px);
  /* font-family: "Bree Serif", serif; */
  display: inline-block;
  background: #ffe6e6;
  border-radius: 5px;
  font-size: 14px;
  padding: 5px;
  color: white;
  margin: 0;
  animation: chan-sh 6s ease infinite;
}

.hint-star {
  display: inline-block;
  margin-left: 0.5em;
  color: gold;
  width: 50%;
}

#container .product-details > p {
  /* font-family: "EB Garamond", serif; */
  /* text-align: center; */
  /* font-size: 18px; */
  color: #7d7d7d;
}
.control {
  bottom: 20%;
  left: 22.8%;
}
.btn {
  transform: translateY(0px);
  transition: 0.3s linear;
  background: #c36a2d;
  overflow: hidden;
  cursor: pointer;
  outline: none;
  border: none;
  color: #eee;
  padding: 0;
  margin: 12px 0;
}

.btn span {
  /* font-family: "Farsan", cursive; */
  transition: transform 0.3s;
  display: inline-block;
  padding: 10px 20px;
  font-size: 1.2em;
  margin: 0;
}
.btn .price,
.shopping-cart {
  background: #333;
  border: 0;
  margin: 0;
}

.btn .price {
  transform: translateX(-10%);
  padding-right: 15px;
}

.btn .shopping-cart {
  transform: translateX(-100%);
  position: absolute;
  background: #333;
  z-index: 1;
  left: 0;
  top: 0;
}

.btn .buy {
  z-index: 3;
  font-weight: bolder;
}

.btn:hover .price {
  transform: translateX(-110%);
}

.btn:hover .shopping-cart {
  transform: translateX(0%);
}
ul {
  list-style: none;
  padding-left: 52px !important;
}
.product-image {
  transition: all 0.3s ease-out;
  display: inline-block;
  position: relative;
  overflow: hidden;
  height: 100%;
  float: right;
  width: 45%;
  display: inline-block;
}

#container img {
  width: 100%;
  height: 100%;
}

.info {
  background: rgba(27, 26, 26, 0.9);
  transition: all 0.3s ease-out;
  transform: translateX(-100%);
  position: absolute;
  line-height: 1.8;
  text-align: left;
  font-size: 105%;
  cursor: no-drop;
  color: #fff;
  height: 100%;
  width: 100%;
  left: 0;
  top: 0;
}

.info h2 {
  text-align: center;
}
.product-image:hover .info {
  transform: translateX(0);
}

.info ul li {
  transition: 0.3s ease;
}

.product-image:hover img {
  transition: all 0.3s ease-out;
}
.product-image:hover img {
  transform: scale(1.2, 1.2);
}
@media (orientation: landscape) {
  body {
    grid-auto-flow: column;
  }
}

/* blog card */
.blog-card {
  display: flex;
  flex-direction: column;
  /* margin: 1rem auto; */
  box-shadow: 0 3px 7px -1px rgba(0, 0, 0, 0.1);
  margin-bottom: 1.6%;
  background: #fff;
  line-height: 1.4;
  /* font-family: sans-serif; */
  /* border-radius: 5px; */
  overflow: hidden;
  z-index: 0;
}
.blog-card a {
  color: inherit;
}
.blog-card a:hover {
  color: #5ad67d;
}
.blog-card:hover .photo {
  transform: scale(1.3) rotate(3deg);
}
.blog-card .meta {
  position: relative;
  z-index: 0;
  height: 200px;
}
.blog-card .photo {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-size: cover;
  background-position: center;
  transition: transform 0.2s;
}
.blog-card .details,
.blog-card .details ul {
  margin: auto;
  padding: 0;
  list-style: none;
}
.blog-card .details {
  position: absolute;
  top: 0;
  bottom: 0;
  left: -100%;
  margin: auto;
  transition: left 0.2s;
  background: rgba(0, 0, 0, 0.6);
  color: #fff;
  padding: 10px;
  width: 100%;
  font-size: 0.9rem;
}
.blog-card .details a {
  text-decoration: dotted underline;
}
.blog-card .details ul li {
  display: inline-block;
}
.blog-card .details .author:before {
  font-family: FontAwesome;
  margin-right: 10px;
  content: "\f007";
}
.blog-card .details .date:before {
  font-family: FontAwesome;
  margin-right: 10px;
  content: "\f133";
}
.blog-card .details .tags ul:before {
  font-family: FontAwesome;
  content: "\f02b";
  margin-right: 10px;
}
.blog-card .details .tags li {
  margin-right: 2px;
}
.blog-card .details .tags li:first-child {
  margin-left: -4px;
}
.blog-card .description {
  padding: 1rem;
  background: #fff;
  position: relative;
  z-index: 1;
}
.blog-card .description h1,
.blog-card .description h2 {
  font-family: Poppins, sans-serif;
}
.blog-card .description h1 {
  line-height: 1;
  margin: 0;
  font-size: 1.7rem;
}
.blog-card .description h2 {
  font-size: 1rem;
  font-weight: 300;
  text-transform: uppercase;
  color: #a2a2a2;
  margin-top: 5px;
}
.blog-card .description .read-more {
  text-align: right;
}
.blog-card .description .read-more a {
  color: #5ad67d;
  display: inline-block;
  position: relative;
}
.blog-card .description .read-more a:after {
  content: ">";
  /* margin-left: -10px; */
  opacity: 0;
  vertical-align: middle;
  transition: margin 0.3s, opacity 0.3s;
}
.blog-card .description .read-more a:hover:after {
  margin-left: 5px;
  opacity: 1;
}
.blog-card p {
  position: relative;
  margin: 1rem 0 0;
}
.blog-card p:first-of-type {
  margin-top: 1.25rem;
}
.blog-card p:first-of-type:before {
  content: "";
  position: absolute;
  height: 5px;
  background: #5ad67d;
  width: 35px;
  top: -0.75rem;
  border-radius: 3px;
}
.blog-card:hover .details {
  left: 0%;
}
@media (min-width: 640px) {
  .blog-card {
    flex-direction: row;
  }
  .blog-card .meta {
    flex-basis: 40%;
    height: auto;
  }
  .blog-card .description {
    flex-basis: 60%;
  }
  .blog-card .description:before {
    transform: skewX(-3deg);
    content: "";
    background: #fff;
    width: 30px;
    position: absolute;
    left: -10px;
    top: 0;
    bottom: 0;
    z-index: -1;
  }
  .blog-card.alt {
    flex-direction: row-reverse;
  }
  .blog-card.alt .description:before {
    left: inherit;
    right: -10px;
    transform: skew(3deg);
  }
  .blog-card.alt .details {
    padding-left: 25px;
  }
}

@media screen and (max-width: 680px) {
  .product-details {
    width: auto !important;
  }
  .product-image {
    float: none;
    width: 100%;
  }
  #container {
    height: auto !important;
    margin-top: 12px;
  }
  .new {
    display: grid;
    grid-template-columns: 1fr;
  }
  .mobile {
    display: none !important;
  }

  .three {
    display: flex;
    justify-content: start;
  }

  .more .main {
    display: grid;
    grid-template-columns: 1fr;
  }
}
</style>
