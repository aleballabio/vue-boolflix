.<template>
  <div class="container">
    <ul class="card">
      <li>
        <h3>Titolo:</h3>
        {{ cardData.title }}
      </li>

      <li>
        <h3>Titolo Originale:</h3>
        {{ cardData.original_title }}
      </li>

      <li>
        <h3>Voto:</h3>
        {{ cardData.vote_average }}
      </li>

      <li>
        <h3>Overview:</h3>
        {{ cardData.overview }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CardFlix",
  props: {
    cardData: Object,
  },
};
</script>

<style scoped lang="scss">
.container {
  background-color: black;
  display: flex;
  padding: 1rem;
  border: solid 1px white;
  flex-basis: calc(100% / 6 - 2rem);

  padding-top: 4rem;
  margin: 1rem;
  height: 500px;
  overflow-y: scroll;
  scrollbar-width: none;
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  list-style: none;

  li {
    font-size: 0.9rem;
    color: white;

    h3 {
      font-size: inherit;
    }
  }
}

.container::-webkit-scrollbar {
  display: none;
}
</style>
