<template>
  <div class="our-service">
    <div class="container-fluid">
      <div class="row">
        <div class="col-5">
          <div class="our-service__gallery">
            <div class="our-service__gallery-card">
              <img
                src="../assets/images/techImgg.jpg"
                class="our-service__gallery-card-img"
              />
              <h5 class="our-service__gallery-card-title">crafts mind</h5>
            </div>
            <div class="our-service__gallery-card">
              <img
                src="../assets/images/techImg.jpg"
                class="our-service__gallery-card-img"
              />
              <h5 class="our-service__gallery-card-title">crafts mind</h5>
            </div>
            <div class="our-service__gallery-card">
              <img
                src="../assets/images/techImgg.jpg"
                class="our-service__gallery-card-img"
              />
              <h5 class="our-service__gallery-card-title">crafts mind</h5>
            </div>
            <div class="our-service__gallery-card">
              <img
                src="../assets/images/techImgg.jpg"
                class="our-service__gallery-card-img"
              />
              <h5 class="our-service__gallery-card-title">crafts mind</h5>
            </div>
            <div class="our-service__gallery-card">
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
