<script setup>
defineProps({
  img: {
    type: String,
    required: true,
  },
  cardTitle: {
    type: String,
    required: true,
  },
  date: {
    type: String,
    required: true,
  },
  categoryID: {
    required: true,
  },
  categoryList: {
    required: true,
  },
});
</script>

<template>
  <div class="generic-card card">
    <div class="generic-card__img-wrapper">
      <img
        :src="img"
        class="generic-card__img"
        alt="card-img"
        @error="ImgNotLoaded($event)"
      />
    </div>
    <div class="generic-card__body">
      <h5 class="generic-card__title">
        {{ cardTitle }}
      </h5>
      <span class="generic-card__date">
        <img
          src="../assets/images/calendar.png"
          class="generic-card__date--icon"
          alt="date-icon"
        />
        {{ moment(date).format("MMMM Do YYYY") }}
      </span>
    </div>
    <div class="generic-card__footer">
      <span class="generic-card__category"> {{ categoryName }}</span>
      <section class="generic-card__actions">
        <img src="../assets/images/heart.png" alt="heart-icon" />
        <img src="../assets/images/share.png" alt="share-icon" />
      </section>
    </div>
  </div>
</template>
<script>
import moment from "moment";
export default {
  data() {
    return {
      categoryName: "",
    };
  },
  methods: {
    ImgNotLoaded(e) {
      e.target.src = "https://picsum.photos/200/300";
    },
    bindCategory() {
      this.categoryName = this.categoryList.filter((item) => {
        // debugger;
        console.log(item, "item");
        if (parseInt(this.categoryID) === item.id) {
          // console.log(this.categoryName.map(item.name));
          return item;
        }
      });
    },
  },
  mounted() {
    this.bindCategory();
  },
};
</script>

<style lang="scss">
//for better clean code we can separate styles into another file
.generic-card {
  border-radius: 24px;
  height: 100%;
  box-shadow: 4px 10px 20px #e6e6e6;
  border: none;

  .generic-card__img-wrapper {
    position: relative;
    &::before {
      display: block;
      content: "";
      width: 100%;
      padding-top: 90%;
      //padding-top: calc((11 / 10) * 100%);
    }

    .generic-card__img {
      border-radius: 24px 24px 0 0;
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }
  }

  .generic-card__body {
    padding: 25px 20px 0 15px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
    flex-grow: 1;

    .generic-card__title {
      color: var(--txt-color);
      font-family: "poppins-bold";
    }

    .generic-card__date {
      color: #707070;
      display: flex;
      align-items: center;

      .generic-card__date--icon {
        width: 15px;
        margin-inline-end: 15px;
      }
    }
  }

  .generic-card__footer {
    display: flex;
    justify-content: space-between;
    padding: 20px;

    .generic-card__category {
      background-color: #74747433;
      font-family: "poppins-regular";
      border-radius: 20px;
      padding: 0 25px;
      color: var(--txt-color);
    }

    .generic-card__actions {
      img {
        width: 15px;
        filter: invert(38%) sepia(49%) hue-rotate(156deg) saturate(37);
        &:first-child {
          margin-inline-end: 10px;
        }
      }
    }
  }
}
</style>
