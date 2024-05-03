sesudah

<template>
  <div class="container">
    <h1>Selamat Datang di Dunia Game</h1>
    <div class="mb-3">
      <label for="inputText" class="form-label">Masukkan Nama Anda</label>
      <input type="text" class="form-control" id="inputText" v-model="inputText" placeholder="Inputkan Sesuatu Disini">
    </div>

    <button class="btn btn-primary" @click="toggleTextStyle">Tebalkan Text</button> &nbsp;
    <button class="btn btn-danger" @click="toggleTextColor">Ubah Warna Text</button> &nbsp;
    <button class="btn btn-warning" @click="toggleTextFont">Ubah Ukuran Text</button>

    <p :class="{ 'text-red': isRedText, 'text-bold': isBoldText, 'text-italic': isItalicText, 
      'text-large': isLargeFont }">{{ inputText }}</p>

    <div class="promotion" :class="{ 'text-bold': isPromotionActive }">
      <h2>Perayaan Hari Game Dunia!</h2>
      <h4>Rayakan bersama kami dengan diskon eksklusif untuk semua game favorit Anda. 
        Banyak Game Game yang menarik untuk dimainkan jangan sampai dilewatkan kesempatan ini !</h4>
      <p>Dapatkan diskon 50% untuk pembelian game premium kami!</p>
      <div class="button-row">
        <button class="btn btn-primary" @click="togglePromotion">Aktifkan Diskon</button>
      </div>
    </div>

    <div class="mb-3">
      <label for="inputEmail" class="form-label">Dapatkan Informasi Terbaru</label>
      <input type="email" class="form-control" id="inputEmail" v-model="email" 
      placeholder="Masukkan alamat email Anda">
    </div>

    <button class="btn btn-success" @click="subscribeToNewsletter">Berlangganan Bersama Kami</button>
    <p :class="{ 'subscribed-message': isSubscribed }" v-if="isSubscribed">Terima kasih! Anda telah berhasil berlangganan.</p>

    <div class="game-list">
      <h2>Daftar Game Yang Diskon</h2>
      <div class="game-item" v-for="game in games" :key="game.id">
        <br><br>
        <h3>{{ game.title }}</h3>
        <button class="btn btn-primary" @click="showGameDetail(game.id)">Lihat Detail</button>
        <div class="game-detail" v-if="selectedGameId === game.id">
          <p><strong>Deskripsi:</strong> {{ game.description }}</p>
          <p><strong>Rating:</strong> {{ game.rating }}</p>
          <p><strong>Genre:</strong> {{ game.genre }}</p>
          <p><strong>Platform:</strong> {{ game.platform }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      isSubscribed: false,
      isPromotionActive: false,
      games: [
        { 
          id: 1, 
          title: 'God Of War', 
          description: 'God of War adalah permainan video aksi-petualangan yang dikembangkan oleh Santa Monica Studio dan diterbitkan oleh Sony Interactive Entertainment. Permainan ini didasarkan pada mitologi Yunani, dan menceritakan kisah dari dewa perang, Kratos, yang mengorbankan keluarganya dan menjadi pembunuh berdarah dingin demi membalas dendam pada dewa Ares. ', 
          rating: 4.8,
          genre: 'Action, Adventure',
          platform: 'PlayStation'
        },
        { 
          id: 2, 
          title: 'Spiderman', 

          description: 'Spider-Man adalah permainan video action-adventure 2018 yang dikembangkan oleh Insomniac Games dan diterbitkan oleh Sony Interactive Entertainment. Ini didasarkan pada karakter superhero Spider-Man Marvel Comics, dan cerita alternatif aslinya yang mengikuti Peter Parker yang berusia 23 tahun dan akhirnya menjadi Spider-Man setelah delapan tahun menekuni identitas tersebut. ', 
          rating: 4.7,
          genre: 'Action, Adventure',
          platform: 'PlayStation, Xbox'
        },
        { 
          id: 3, 
          title: 'Panda', 
          description: 'Panda adalah permainan video strategi simulasi yang dikembangkan oleh Bamboo Games. Dalam permainan ini, pemain bertugas merawat dan mengembangkan kebun binatang dengan spesialisasi pada panda. Pemain harus memastikan panda-panda tersebut bahagia dan sehat sambil menjaga kebun binatang agar tetap berjalan dengan lancar.', 
          rating: 4.5,
          genre: 'Strategy, Simulation',
          platform: 'PC, Nintendo Switch'
        }
      ],
      selectedGameId: null,
      inputText: '',
      isRedText: false,
      isBoldText: false,
      isItalicText: false,
      isLargeFont: false,
      textColor: 'black',
      textStyle: 'normal',
      textFont: '16px'
    };
  },
  methods: {
    toggleTextColor() {
      this.isRedText = !this.isRedText;
      if (this.isRedText) {
        this.textColor = 'red';
      } else {
        this.textColor = 'black';
      }
    },
    toggleTextStyle() {
      this.isBoldText = !this.isBoldText;
      if (this.isBoldText) {
        this.textStyle = 'bold';
      } else {
        this.textStyle = 'normal';
      }
    },
    toggleTextFont() {
      this.isLargeFont = !this.isLargeFont;
      if (this.isLargeFont) {
        this.textFont = '30px';
      } else {
        this.textFont = '16px';
      }
    },
    togglePromotion() {
      this.isPromotionActive = !this.isPromotionActive;
    },
    subscribeToNewsletter() {
      this.isSubscribed = true;
    },
    showGameDetail(gameId) {
      if (this.selectedGameId === gameId) {
        this.selectedGameId = null;
      } else {
        this.selectedGameId = gameId;
      }
    }
  }
}
</script>
