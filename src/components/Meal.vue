<template>
  <div class="container">
    <div class="btnDiv">
      <button @click="fetchMeal" class="btn">Get Random Meal</button>
    </div>

    <div class="image">
      <img :src="image" :alt="title" />
    </div>

    <div class="meal-info">
      <div class="title header-text">
        <h2>{{ title }}</h2>
      </div>
      <div>
        <b class="header-text">Category: </b> <span>{{ category }} </span>
      </div>

      <div v-if="this.mealTags">
        <b class="header-text">Tag(s): </b>
        <em>{{ mealTags }}</em>
      </div>
    </div>

    <div class="details">
      <div>
        <h3 class="header-text">Ingredients</h3>
        <ul v-for="item in ingredients" :key="item">
          <li>{{ item }}</li>
        </ul>
      </div>

      <div>
        <h3 class="header-text">Instructions</h3>
        <p>{{ instructions }}</p>
      </div>
    </div>

    <div>
      <h3 class="header-text">Step by Step Video Guide</h3>

      <div class="video">
        <iframe
          type=""
          width="640"
          height="360"
          :src="videoUrl"
          frameborder="0"
        ></iframe>
      </div>
    </div>

    <div class="source">
      <h6>Source: <a :href="source"> {{ source }} </a></h6>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Meal",
  data() {
    return {
      id: "",
      category: "",
      image: "",
      ingredients: [],
      instructions: "",
      mealTags: "",
      source: "",
      title: "",
      videoUrl: "",
      items: ""
    };
  },

  methods: {
    async fetchMeal() {
      try {
        const res = await axios.get(
          "https://www.themealdb.com/api/json/v1/1/random.php"
        );

        const { meals } = res.data;

        // console.log("iii", meals[0].strCategory);
        this.category = meals[0].strCategory;
        this.title = meals[0].strMeal;
        this.instructions = meals[0].strInstructions;
        this.image = meals[0].strMealThumb;
        this.source = meals[0].strSource;
        this.mealTags = meals[0].strTags;
        this.videoUrl = `https://www.youtube.com/embed/${meals[0].strYoutube.slice(
          -11
        )}`;

        this.ingredients = [];
        for (let i = 1; i <= 20; i += 1) {
          if (meals[0][`strIngredient${i}`]) {
            this.ingredients.push(
              meals[0][`strIngredient${i}`] + " - " + meals[0][`strMeasure${i}`]
            );
          } else {
            break;
          }
        }
      } catch (error) {
        console.log("ERROR: ", error);
      }
    }
  },
  mounted() {
    this.fetchMeal();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  margin: 2em 0 0;
}

.btnDiv {
  text-align: center;
}

.image {
  margin-top: 1em;
  padding: 1em 0;
  width: 100%;
  height: 80vh;
}

img {
  width: 100%;
  border-radius: 4px;
  height: -webkit-fill-available;
}

.meal-info div {
  padding-bottom: 1em;
}

.title {
  text-transform: uppercase;
}

.header-text {
  color: rgb(8, 66, 66);
  padding-bottom: 1em;
}

.details {
  padding: 2em 0;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.details div {
  width: 50%;
  line-height: 30px;
}

li {
  padding-bottom: 0.5em;
}

.video {
  width: 100%;
  height: 60vh;
}

iframe {
  width: 100%;
  height: 100%;
  border-radius: 4px;
}

.source {
  padding: 1em 1em;
  background: white;
  text-align: end;
}

@media screen and (max-width: 780px) {
  .details {
    padding: 1em 0;
  }

  .details div {
    width: 100%;
    line-height: 30px;
  }

  .details div:nth-of-type(2) {
    padding-top: 1em;
  }

  li {
    padding-bottom: 0.3em;
  }

  .title {
    font-size: 0.7em;
    text-decoration: underline;
  }

  .header-text {
    padding-bottom: 0.3em;
  }

  .image {
    margin: 1em 0;
    padding: 0;
    height: 50vh;
  }

  .video {
    height: 50vh;
  }
}
</style>
