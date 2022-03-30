.<template>
  <div
    class="container"
    @mouseover="showImage = false"
    @mouseleave="showImage = true"
  >
    <img v-show="showImage === true" :src="setImage()" :alt="cardData.title" />
    <ul class="card" v-show="showImage === false">
      <li>
        <h3>Titolo:</h3>
        {{ cardData.title }}
      </li>

      <li>
        <h3>Titolo Originale:</h3>
        {{ cardData.original_title }}
      </li>

      <li>
        <h3>Lingua Originale:</h3>
        <lang-flag :iso="cardData.original_language" class="flag" />
      </li>

      <li>
        <h3>Voto:</h3>
        <star-rating
          :rating="ratingFiveNumber()"
          :inline="true"
          :star-size="15"
          :read-only="true"
          :increment="1"
          :max-rating="5"
          :round-start-rating="true"
          :show-rating="false"
        >
        </star-rating>
      </li>

      <li>
        <h3 v-show="cardData.overview != ''">Overview:</h3>
        {{ cardData.overview }}
      </li>
    </ul>
  </div>
</template>

<script>
import StarRating from "vue-star-rating";
import coverNone from "../assets/cover.jpg";
export default {
  name: "CardFlix",

  components: {
    StarRating,
  },
  data() {
    return {
      showImage: true,
      ratingFiveStars: this.cardData.vote_average,
    };
  },
  props: {
    cardData: Object,
  },

  methods: {
    ratingFiveNumber() {
      let maxVote = 10;
      let wantedVote = 5;
      let convertedRating = Math.ceil(
        (this.cardData.vote_average * wantedVote) / maxVote
      );
      return convertedRating;
    },

    setImage() {
      if (this.cardData.poster_path == null) {
        return coverNone;
      } else {
        return "http://image.tmdb.org/t/p/w500/" + this.cardData.poster_path;
      }
    },
  },
};
</script>

<style scoped lang="scss">
.container {
  background-color: black;
  flex-basis: calc(100% / 5 - 2px);
  align-self: center;
  display: flex;

  border: solid 1px transparent;
  border-radius: 2px;
  margin-left: 1px;
  margin-right: 1px;
  margin-bottom: 4rem;
  height: 500px;

  overflow-y: scroll;
  scrollbar-width: none;
  -ms-overflow-style: none;
  scrollbar-width: none;

  img {
    width: 100%;
    height: 100%;
    object-position: center;
  }
}

.card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  list-style: none;
  padding-top: 4rem;
  padding-left: 1rem;
  padding-right: 1rem;
  margin-bottom: 4rem;

  li {
    font-size: 0.9rem;
    color: white;

    h3 {
      font-size: inherit;
      padding-right: 0.3rem;
    }
  }
}

.container::-webkit-scrollbar {
  display: none;
}

.flag {
  margin-left: 0.5rem;
}
</style>
