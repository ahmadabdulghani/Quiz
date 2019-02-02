<template>
  <div class="hello">
    <h1 v-if="show">{{ msg }}</h1>
    <h1 v-else>Judul Disembunyikan</h1>

    <p>{{ nama }}</p>

    <input type="text" v-model="nama">

    <button type="button" v-on:click="hideTitle">Click Me</button><br><br><br>
    <h2>{{ "Skor Anda "+poin }}</h2>

    <div v-for="(item,index) in items" :key="item.pertanyaan" :option="item.pertanyaan">
      <p>{{ item.pertanyaan }}</p>
      <div v-for="pilih in item.pilihan" :key="pilih.pilihan" :option="pilih.pilihan">
        <input type="radio" name="data['+index+']" v-on:click="checkJawaban(index,pilih.pilihan)" :value="pilih.pilihan" v-model="answer">{{ pilih.pilihan }}
      </div><br><br>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function(){
    return {
      nama: 'Ghani',
      poin: 0,
      answer:String,
      show: true,
      items : [
      {
        name: 'soal1',
        pertanyaan: '1. 4 + 5 =',
        jawab: String,
        check:false,
        pilihan: [
        { pilihan: '10' },
        { pilihan: '12' },
        { pilihan: '7'  },
        { pilihan: '9'  }
        ],
        jawaban:'9'
      },
      {
        name: 'soal2',
        pertanyaan: '2. Sepak bola dimainkan berapa orang ?',
        jawab: String,
        pilihan:[
        { pilihan: '8 orang'  },
        { pilihan: '9 orang'  },
        { pilihan: '11 orang' },
        { pilihan: '10 orang' }
        ],
        jawaban:'11 orang'
      },
      {
        name: 'soal3',
        pertanyaan: '3. Ibu kota Indonesia adalah ?',
        jawab: String,
        pilihan: [
        { pilihan: 'Bandung'  },
        { pilihan: 'Jakarta'  },
        { pilihan: 'Surabaya' },
        { pilihan: 'Makassar' }
        ],
        jawaban: 'Jakarta'
      }
      ] 
    }
  },
  methods: {
    hideTitle () {
      this.show = !this.show
    
  },

  checkJawaban(i, answer){
    if (this.items[i].jawaban === answer) {
      this.poin++;
    }
  }
},
  mounted: function () {
    this.nama = 'Suwita'
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
