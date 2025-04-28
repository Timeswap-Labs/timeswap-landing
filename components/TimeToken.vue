<template>
  <section :class="$style.featurePage">
    <div :class="$style.content">
      <!-- <h2 :class="$style.mainTitle">Time Token</h2> -->
      <div :class="$style.tokenImage">
        <img :class="['animateMe']" src="@/assets/images/timetoken.svg" alt />
        <img
          :class="[$style.mobile, 'animateMe']"
          src="@/assets/images/timetoken-mobile.svg"
          alt
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss" module>
.featurePage {
  position: relative;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  min-height: 80vh;
  box-sizing: border-box;

  .content {
    width: 100vw;
    height: 80vh;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
    padding: 0;

    .tokenImage {
      width: 100vw;
      height: 80vh;
      display: flex;
      align-items: center;
      justify-content: center;

      img {
        width: 90vw;
        height: 80vh;
        max-width: none;
        max-height: 80vh;
        object-fit: contain;
        display: block;

        @include media-breakpoint-down(sm) {
          display: none;
        }
      }

      .mobile {
        display: none;
        @include media-breakpoint-down(sm) {
          display: block;
          width: 90vw;
          height: auto;
          max-width: 100vw;
        }
      }
    }
  }
}
</style>
