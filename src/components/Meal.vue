<template>
  <div class="container">
    <div class="btnDiv">
      <button @click="fetchMeal" class="btn">Click here</button>
    </div>

    <div class="image">
      <img :src="image" :alt="title" />
    </div>

    <div class="meal">
      <h2>{{ title }}</h2>

      <div>
        <b>Category: </b> <span>{{ category }} </span>
      </div>

      <div>
        <h3>Instructions</h3>
        <p>{{ instructions }}</p>
      </div>

      <span>
        <em>{{ mealTags }}</em>
      </span>

      <div>
        <iframe
          type=""
          width="640"
          height="360"
          :src="videoUrl"
          frameborder="0"
        ></iframe>
      </div>

      <div>
        <h3><span>ingredients :</span></h3>
        <ul v-for="item in ingredients" :key="item">
          <li>{{ item }}</li>
        </ul>
      </div>

      <div>
        <h6>Source: {{ source }}</h6>
      </div>
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

        console.log("iii", meals[0].strCategory);
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
  margin: 2em 0;
}

.btnDiv {
  text-align: center;
}

.image {
  padding: 1em 0;
  width: 100%;
}

img {
  width: 100%;
  border-radius: 4px;
  height: 40vh;
}

iframe {
  border-radius: 4px;
}
</style>
