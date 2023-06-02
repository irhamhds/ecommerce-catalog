<template>
  <section class="men-section" >
  <div class="container">
    <div class="img">
      <img src="../assets/image 2.png" alt="men clothing">
    </div>
    <div class="decription">
    <div v-if="product" >
      <h2>{{ product.title }}</h2>
      <p>{{ product.category }}</p>
      <p>{{ product.rating }}</p><hr>
      <div class="text"><p>{{ product.description }}</p></div>
      <p class="price">${{product.price}}</p>
    </div>
  </div>
    <button @click="fetchProduct">Next Product</button> 
  </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      product:null,
      index: 1,
      category : ["men's clothing","women's clothing","page-unavailable"],
      price :"price",
      rating :[{rate:2.6, count:235}]
    };
  },
  methods: {
    fetchProduct() {
      fetch(`https://fakestoreapi.com/products/${this.index}`)
      .then((response) => response.json())
      .then((data) => {
          if (data.category === "men's clothing" || data.category === "women's clothing") {
            this.product = data;
          } else {
            this.product = null;
          }
        this.index = this.index >= 20 ? 1 : this.index + 1;
        })
      },
    },
  };
</script>

<style>
.men-section {
display: flex;
position: absolute;
width: 1283px;
height: 450px;
left: -3px;
top: 0px;
background-image: url("../assets/Rectangle 5.png");
}
.container {
width: 800px;
display: flex;
padding: 12px, 8px;
position: absolute;
width: 1000px;
height: 380px;
left: 125px;
top: 150px;
background: #FFFFFF;
box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
border-radius: 10px 20px;
}  
.img {
display: flex;
flex: 1 2;
justify-content: center;
justify-items: center;
width: 50%;
justify-content: space-between;
}
.decription /* > .container > .img */{
display: flex;
flex: 1 30px;
width: 50%;
padding-top: 12px;
justify-content: space-between;
}
p {
  display: inline;
}
.price{
display: block;
font-family: 'Inter';
font-style: normal;
font-weight: 600;
font-size: 28px;
line-height: 34px;
color: #002772;
}
.text {
font-family: 'Inter';
font-style: normal;
font-weight: 400;
font-size: 20px;
line-height: 24px;
}
button {
cursor: pointer;
display: flex;
text-align: center;
color: #002772;
box-sizing: border-box;
position: absolute;
width: 200px;
height: 45px;
left: 720px;
top: 290px;
padding: 15px 5px 35px ;
background: #FFFFFF;
border: 3px solid #002772;
border-radius: 4px;
margin-bottom: 50px;
}
.women-section {
position: absolute;
width: 1283px;
height: 548px;
left: -3px;
top: 0px;
background: #FDE2FF;
}
.container2 {
position: absolute;
width: 1283px;
height: 548px;
left: -3px;
top: 0px;
background: #FDE2FF;
}
.page-unavailable {
position: absolute;
width: 1283px;
height: 548px;
left: -3px;
top: 0px;
background: #D8D7D7;
}
</style>
