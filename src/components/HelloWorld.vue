<template>
  <div class="hello">
    <h2> {{ pesanBindView }} </h2>
    <input v-bind:value="pesanBindAttribute1" /> <br/>
    <img v-bind:src="pesanBindAttribute2" /> <br/>
    <input v-model="pesanBindDuaArah1" /> <br/>
    <p>Hasil pesanBindDuaArah1: {{ pesanBindDuaArah1 }} </p><br/>

    <button v-on:click="alertEvent(pesanBindEvent1)"> Event Bind Klik Aku </button> <br/>
    <input type="text" placeholder="Event 2" v-on:change="alertEvent(pesanBindEvent2)"> <br/>
    <input placeholder="Event 3"  v-on:keyup.enter="alertEvent(pesanBindEvent3)"  /> <br/>
    <p>{{ info }}</p>
    <p>{{ errored }}</p>
    <hr/>
    penjumlahan: <br>
    masukkan angka pertama: <input v-model="angkaPertama" /> <br>
    masukkan angka kedua: <input v-model="angkaKedua"/> <br>
    hasilnya: {{ hasilTambah }}
    <hr/>
    pengurangan: <br>
    masukkan angka pertama: <input v-model="angkaPertama" /> <br>
    masukkan angka kedua: <input v-model="angkaKedua"/> <br>
    hasilnya: {{ hasilKurang }}
  </div>
</template>

<script>
import { API } from "../Constants";
import axios from  'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      pesanBindView: 'Halo Ini Binding ke view',
      pesanBindAttribute1: 'Ini value dari input',
      pesanBindAttribute2: 'https://akcdn.detik.net.id/'+
                          'community/media/visual/2016/01/21/10d0bf99-b67b-420b-b0bf-a05153019435_43.jpg',
      pesanBindDuaArah1: 'Value awal',
      pesanBindEvent1: 'Muncul dari On Click',
      pesanBindEvent2: 'Muncul dari On Change',
      pesanBindEvent3: 'Kamu barusan tekan enter',
      angkaPertama: 0,
      angkaKedua: 0,
      angkaHasil: 0,

      loading: true,
      errored: false,
      info: 'String'
    }
  },
  mounted() {
    
  },
  computed: {
    hasilTambah() {
      this.angkaHasil = parseInt(this.angkaPertama) + parseInt(this.angkaKedua);
      return this.angkaHasil;
    },
    hasilKurang() {
      this.angkaHasil = parseInt(this.angkaPertama) - parseInt(this.angkaKedua);
      return this.angkaHasil;
    }
  },
  methods: {
    alertEvent(params) {
      alert(params)
    }
  }
}
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
