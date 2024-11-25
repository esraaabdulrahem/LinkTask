<template>
  <div class="home-page">
    <div class="banner-container">
      <Banner />
    </div>
    <OurServices />
    <div class="container">
      <div class="latest-news">
        <h6 class="generic-sub-title">Media</h6>
        <h1 class="latest-news__title">Top News</h1>
        <div class="latest-news__categories">
          <button
            v-for="category in categoryList"
            :key="category.id"
            @click="getClickedCategory(category.id)"
          >
            {{ category.name }}
          </button>
        </div>
        <div class="row row-gap-5">
          <div
            v-for="(item, index) in initailNewsListingArray"
            :key="index"
            class="col-md-4"
          >
            <GenericCard
              :categoryID="item.categoryID"
              :categoryList="categoryList"
              :img="item.urlToImage"
              :cardTitle="item.title"
              :date="item.publishedDate"
            />
          </div>
        </div>
        <button class="generic-orange-btn" @click="viewAll">View all news</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import GenericCard from "../components/GenericCard.vue";
import Banner from "../components/Banner.vue";
import OurServices from "@/components/OurServices.vue";
export default {
  components: {
    GenericCard,
    Banner,
    OurServices,
  },
  data() {
    return {
      newsList: [],
      categoryList: [],
      formatedDate: "",
      filteredNewsList: [],
      categoryName: "",
      initailNewsListingArray: [],
    };
  },
  methods: {
    async latestNewsList() {
      await axios.get("https://api.npoint.io/d275425a434e02acf2f7").then((res) => {
        console.log(res, "respons");
        this.newsList = res.data.News;
        this.initailNewsListingArray = this.newsList.slice(0, 6);
      });
      console.log(this.newsList, "newslist");
    },
    async getAllCategories() {
      await axios.get("https://api.npoint.io/91298d970c27e9a06518").then((res) => {
        // console.log(res, "respons");

        this.categoryList = res.data.newsCategory;
        return this.categoryList;
      });
      // console.log(this.categoryList, "newslist");
    },
    resetFilter() {
      this.initailNewsListingArray = [];
      this.initailNewsListingArray = this.newsList;
    },
    getClickedCategory(categoryID) {
      debugger;
      this.resetFilter();
      this.initailNewsListingArray.filter((item) => {
        // debugger;
        console.log(categoryID, "categoryID");
        console.log(parseInt(item.categoryID), "parseInt(item.categoryID");
        console.log(
          parseInt(item.categoryID) === categoryID,
          "(parseInt(item.categoryID) === categoryID)"
        );
        if (parseInt(item.categoryID) === categoryID) {
          debugger;
          this.filteredNewsList.push(item);
        }
      });
      this.initailNewsListingArray = [];
      this.initailNewsListingArray = this.filteredNewsList;
    },
    viewAll() {
      console.log(this.newsList, "viewAll");
      this.initailNewsListingArray = [];
      this.initailNewsListingArray = this.newsList;
    },
  },
  async mounted() {
    await this.latestNewsList();
    await this.getAllCategories();
  },
};
</script>
