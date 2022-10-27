<template>
  <div class="container hello">
    <h1>{{ msg }}</h1>
    <div class="col-md-6 mx-auto">
      <div class="input-group my-5">
        <input
          v-model="searchingCode"
          placeholder="BARKOD OKUT"
          ref="barkodInput"
          type="text"
          class="form-control py-3"
          aria-describedby="button-addon2"
        />
        <div class="input-group-append">
          <button
            @click="clearForm"
            class="btn btn-outline-secondary py-3"
            type="button"
            id="button-addon2"
          >
            TEMİZLE
          </button>
          <button
            @click="sendData"
            class="btn btn-outline-secondary py-3"
            type="button"
            id="button-addon2"
          >
            ÜRÜN EKLE
          </button>
          <button
            @click="getData"
            class="btn btn-outline-secondary py-3"
            type="button"
            id="button-addon2"
          >
            FİYAT SORGULA
          </button>
        </div>
      </div>
    </div>

    <div class="col-md-8 mx-auto">
      <table class="table table-bordered">
        <thead class="thead-dark">
          <tr>
            <th scope="col">#</th>
            <th scope="col">Barkod</th>
            <th scope="col">Ürün Adı</th>
            <th scope="col">Adet</th>
            <th scope="col">Fiyat</th>
          </tr>
        </thead>
        <tbody v-for="(i, index) in prodsArray" :key="index">
          <tr v-if="searchingCode == i.prodCode" style="font-size: 20px">
            <th scope="row">{{ index }}</th>
            <td>{{ i.prodCode }}</td>
            <td>{{ i.prodName }}</td>
            <td>1 adet</td>
            <td>{{ i.prodPrice }} TL</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "BaseSearhArea",
  props: {
    msg: String,
  },
  data: function () {
    return {
      searchingCode: "",
      searchingCodeTemp: "",
      prodsArray: [],
      mydata: {
        prodCode: "8690826425501",
        prodName: "Faber Castell Tükenmez Kalem 1425",
        prodCategory: "kalem",
        prodPrice: "12.50",
      },
    };
  },
  methods: {
    sendData(e) {
      e.preventDefault();
      console.log(this.mydata);
      axios.post(
        "https://uk-product-db-default-rtdb.firebaseio.com/posts.json",
        this.mydata
      );
    },
    getData(w) {
      w.preventDefault();
      this.prodsArray = [];
      console.log("start");
      axios
        .get("https://uk-product-db-default-rtdb.firebaseio.com/posts.json")
        .then((response) => {
          let data = response.data;
          for (let key in data) {
            this.prodsArray.push({ ...data[key], id: key });
            console.log("continue");
            console.log(this.prodsArray);
          }
        })
        .catch((e) => console.log(e));
      console.log("end");
    },
    clearForm() {
      this.$refs["barkodInput"].value = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
