<template>
  <div class="col-md-8 mx-auto">
    <table class="table table-bordered">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Ürün Adı</th>
          <th scope="col">Adet</th>
          <th scope="col">Fiyat</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(i, index) in prodsArray" :key="index">
          <th scope="row">{{ index }}</th>
          <td>{{ i.prodName }}</td>
          <td>1 adet</td>
          <td>{{ i.prodPrice }} TL</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: "BaseListArea",
  data: function () {
    return {
      prodsArray: [
        {
          prodName: "PENSAN BÜRO TÜKENMEZ KALEM 1MM 2270 MAVİ 50 Lİ",
          prodCategory: "kalem",
          prodPrice: "55",
        },
        {
          prodName: "Rotring Versatil Kalem Tikky 0.7 mm Siyah 1904696",
          prodCategory: "kalem",
          prodPrice: "22,90",
        },
        {
          prodName: "PENSAN TÜKENMEZ TRIBALL 1MM RENKLİ 8 Lİ SET 01003",
          prodCategory: "kalem",
          prodPrice: "15,51",
        },
      ],
    };
  },
};
</script>

<style></style>
