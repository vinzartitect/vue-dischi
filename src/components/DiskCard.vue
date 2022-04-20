<template>
    <div class="card">
        <!-- richiamo i dati api dal props -->
        <img :src="poster" :alt="title">
        <h3>{{title}}</h3>
        <span>{{author}}</span>
        <span>{{year}}</span>
    </div>
</template>

<script>
export default {
  name: 'DiskCard',
  props: {
    // richiamo le singole voci api presenti nel componente padre 
      poster: String,
      title: String,
      author: String,
      year: String,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .card {
        width: calc(20% - 40px);
        background-color: #2e3a46;
        margin: 0 20px 30px;
        padding: 20px;
        text-align: center;
        transition: all .1s ease;
        cursor: pointer;
        img {
            width: 100%;
            margin-bottom: 15px;
        }
        h3 {
            margin-bottom: 15px;
            color: white;
            font-size: 1rem;
            text-transform: uppercase;
        }
        span {
            display: block;
            color: #777d7a;
            font-size: .9rem;
        }
        &:hover {
            transform: scale(1.05);
        }
    }
</style>