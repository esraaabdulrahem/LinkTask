<template>
  <div class="our-service">
    <div class="container-fluid">
      <div class="row">
        <div class="col-5">
          <div class="our-service__gallery">
            <div class="our-service__gallery-card">
              <div class="overlay"></div>
              <p class="overlay-text">
                <img src="../assets/images/right-arrow.png" />
                Hello World
              </p>
              <img
                src="../assets/images/techImgg.jpg"
                class="our-service__gallery-card-img"
              />
              <h5 class="our-service__gallery-card-title">crafts mind</h5>
            </div>
          </div>
        </div>
        <div class="col-7">
          <div class="our-service__content">
            <h1 class="our-service__content--title">We Deliver Digital Productivity</h1>
            <p class="our-service__content--brief">
              We craft technology solutions that digitally bond and transform the
              productivity of our customers and their citizens, workers, consumers and
              partners.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import mockApi from "../../services/mockApiData.json";
export default {
  data() {
    return {
      serviceList: {},
    };
  },
};
</script>
<style lang="scss">
//for better clean code we can separate styles into another file
.our-service {
  background-color: #efefef;
  padding: 110px 0 135px 0;
  .our-service__gallery {
    .our-service__gallery-card {
      position: relative;
      max-width: 250px;
      height: 250px;
      .overlay {
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        height: 100%;
        width: 100%;
        opacity: 0;
        transition: 0.5s ease;
        background-color: #169cc9;
      }
      .overlay-text {
        display: none;
        img {
          width: 20px;
          filter: invert(0);
        }
      }
      &:hover {
        .overlay {
          opacity: 0.5;
        }
        .overlay-text {
          display: block;
          position: absolute;
          color: var(--vt-c-white);
        }
      }
      .our-service__gallery-card-img {
        width: 100%;
        height: 100%;
      }
      .our-service__gallery-card-title {
        position: absolute;
        bottom: 0;
        z-index: 20;
        color: var(--vt-c-white);
      }
    }
  }

  .our-service__content {
    background-color: var(--pink-color);
    padding: 60px 70px;
    text-align: end;
    .our-service__content--title {
      color: #253776;
      font-size: 55px;
    }
    .our-service__content--brief {
      color: var(--vt-c-white);
      font-size: 27px;
      padding: 0 0 0 50px;
    }
  }
}
</style>
