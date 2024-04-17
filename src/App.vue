<template>
  <div id="app">
    <h1 class="title-app">Vue Quiz App</h1>

    <Quiz
      :quizData="quizData"
      v-if="quizData.length > 0"
      @answer-selected="updateProgressAndMessage"
    />
  </div>
</template>

<script>
import Quiz from "./components/Quiz.vue";

export default {
  name: "App",
  components: {
    Quiz,
  },
  data() {
    return {
      quizData: [
        {
          question: "Apa singkatan dari HTML?",
          options: [
            "Hyper Text Markup Language",
            "Hyperlink Text Management Language",
            "High Technology Markup Language",
            "Hyperlink Technical Management Language",
          ],
          correctAnswer: "Hyper Text Markup Language",
        },
        {
          question: "Apa singkatan dari CSS?",
          options: [
            "Cascading Style Sheet",
            "Creative Style Sheet",
            "Computer Style Sheet",
            "Colorful Style Sheet",
          ],
          correctAnswer: "Cascading Style Sheet",
        },
        {
          question: "Apa singkatan dari API?",
          options: [
            "Application Programming Interface",
            "Advanced Programming Interface",
            "Automated Program Integration",
            "Application Program Interface",
          ],
          correctAnswer: "Application Programming Interface",
        },
        {
          question: "Apa kepanjangan dari HTTP?",
          options: [
            "Hyper Transfer Text Protocol",
            "Hyper Text Transfer Protocol",
            "High Transfer Text Protocol",
            "Hyper Technical Transfer Protocol",
          ],
          correctAnswer: "Hyper Text Transfer Protocol",
        },
        {
          question: "Apa fungsi dari JavaScript?",
          options: [
            "Mengatur tata letak halaman web",
            "Membuat animasi",
            "Mengolah data di sisi server",
            "Menambahkan interaktivitas ke halaman web",
          ],
          correctAnswer: "Menambahkan interaktivitas ke halaman web",
        },
        {
          question: "Apa yang dimaksud dengan Array dalam pemrograman?",
          options: [
            "Sebuah jenis variabel yang menyimpan satu nilai tunggal",
            "Sebuah perintah untuk menambahkan elemen ke halaman web",
            "Sebuah struktur data yang menyimpan kumpulan nilai yang terkait",
            "Sebuah jenis fungsi yang digunakan untuk menghitung nilai matematika",
          ],
          correctAnswer:
            "Sebuah struktur data yang menyimpan kumpulan nilai yang terkait",
        },
        {
          question: "Apa singkatan dari SQL?",
          options: [
            "Structured Query Language",
            "Sequential Query Language",
            "Standard Query Language",
            "Software Query Language",
          ],
          correctAnswer: "Structured Query Language",
        },
        {
          question: "Apa kegunaan dari git dalam pengembangan perangkat lunak?",
          options: [
            "Mengatur database",
            "Membuat desain grafis",
            "Mengontrol versi kode sumber",
            "Mengelola server",
          ],
          correctAnswer: "Mengontrol versi kode sumber",
        },
        {
          question: "Apa singkatan dari URL?",
          options: [
            "Uniform Resource Locator",
            "Universal Resource Locator",
            "Uniform Resource Link",
            "Universal Resource Link",
          ],
          correctAnswer: "Uniform Resource Locator",
        },
        {
          question: "Apa yang dimaksud dengan looping dalam pemrograman?",
          options: [
            "Proses menjalankan program dari awal",
            "Pengulangan satu atau beberapa pernyataan",
            "Mengubah tampilan aplikasi",
            "Membuat variasi warna pada elemen",
          ],
          correctAnswer: "Pengulangan satu atau beberapa pernyataan",
        },
      ],
    };
  },
};
</script>
