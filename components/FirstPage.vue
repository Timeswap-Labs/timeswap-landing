<template>
  <section :class="$style.firstPage">
    <div :class="$style.content">
      <h1 id="bigtitle" :class="$style.mainTitle">
        Permissionless DeFi infrastructure for capturing time value of any asset
        <span :class="$style.highlight">{{ currentAsset }}</span>
      </h1>
      <div :class="$style.chainList">
        <span style="width: 100%; margin-bottom: 8px">Live on</span>

        <div
          v-for="(supportedChain, index) in supportedChains"
          :key="index"
          :class="$style.supportedChain"
        >
          <img
            :src="getImgUrl(supportedChain.image)"
            :alt="supportedChain.name"
            height="24px"
          />
          <span :class="$style.chainName">{{ supportedChain.name }}</span>
          <span v-if="supportedChain.soon" :class="$style.soonBadge">Soon</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      assets: [
        'HYPE',
        'PURR',
        'HFUN',
        'BTC',
        'ETH',
        'PENDLE',
        'COOK',
        'VIRTUAL',
        'AIXBT',
      ],
      currentAsset: 'HYPE',
      assetIndex: 0,
      intervalId: null,
      supportedChains: [
        {
          name: 'HyperEVM',
          image: 'hyperevm',
        },
        {
          name: 'Arbitrum',
          image: 'ARB',
        },
        {
          name: 'Mantle',
          image: 'MANTLE',
        },
        {
          name: 'Base',
          image: 'BASE',
        },
        {
          name: 'Optimism',
          image: 'OP',
        },
        {
          name: 'Ethereum',
          image: 'ETH',
        },
        {
          name: 'Polygon',
          image: 'MATIC',
        },
        {
          name: 'Berachain Testnet',
          image: 'beratest',
        },
      ],
    }
  },
  mounted() {
    this.animateAssets()
  },
  beforeDestroy() {
    clearInterval(this.intervalId)
  },
  methods: {
    getImgUrl(icon) {
      return require(`@/assets/images/chains/${icon}.png`)
    },
    animateAssets() {
      this.intervalId = setInterval(() => {
        this.assetIndex = (this.assetIndex + 1) % this.assets.length
        this.currentAsset = this.assets[this.assetIndex]
      }, 2000) // Change text every 2 seconds
    },
  },
}
</script>

<style lang="scss" module>
.firstPage {
  padding: 100px 0;
  position: relative;
  padding-left: 160px;
  display: flex;
  align-items: center;

  @include media-breakpoint-down(lg) {
    padding-left: 100px;
  }

  @include media-breakpoint-down(md) {
    padding: 80px 0;
    padding-left: 50px;
  }

  @include media-breakpoint-down(sm) {
    width: 100%;
    padding: 120px 24px 100px;
    height: 100vh;
    text-align: center;
  }

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 50%;
    height: 100%;
    background: url('@/assets/images/first-bg.png');
    background-size: cover;
    background-position: left;

    @include media-breakpoint-down(md) {
      background-position: center;
    }

    @include media-breakpoint-down(sm) {
      display: none;
    }
  }

  &::after {
    content: '';
    position: absolute;
    top: 0;
    right: -20%;
    width: 50%;
    height: 100%;
    background: url('@/assets/images/hm-right-side.png') no-repeat;
    background-size: 100% 100%;

    @include media-breakpoint-down(lg) {
      right: -10%;
    }

    @include media-breakpoint-down(sm) {
      right: 0;
    }

    @include media-breakpoint-down(sm) {
      display: none;
    }
  }

  .rightArrow {
    position: absolute;
    background: url('@/assets/images/right-arrow.svg') no-repeat;
    width: 43px;
    height: 44px;
    right: 160px;
    top: 50%;
    transform: translateY(-50%);
    animation: bounce 3s infinite;

    @keyframes bounce {
      0%,
      20%,
      50%,
      80%,
      100% {
        transform: translateX(0);
      }

      40% {
        transform: translateX(-20px);
      }

      60% {
        transform: translateX(-10px);
      }
    }

    @keyframes bounceY {
      0%,
      20%,
      50%,
      80%,
      100% {
        transform: translate(-50%, 0) rotate(90deg);
      }

      40% {
        transform: translate(-50%, -20px) rotate(90deg);
      }

      60% {
        transform: translate(-50%, -10px) rotate(90deg);
      }
    }

    @include media-breakpoint-down(lg) {
      right: 100px;
    }

    @include media-breakpoint-down(md) {
      right: 50px;
    }

    @include media-breakpoint-down(sm) {
      right: initial;
      left: 50%;
      top: initial;
      bottom: 60px;
      animation: bounceY 3s infinite;
    }
  }

  .content {
    width: 100%;
    max-width: 900px;
    position: relative;
    z-index: 9;

    @include media-breakpoint-down(lg) {
      max-width: 100%;
    }

    @include media-breakpoint-down(md) {
      max-width: 80%;
    }

    @include media-breakpoint-down(sm) {
      max-width: 100%;
    }

    .subTitle {
      line-height: 1.5;
      color: $secondary;
    }

    .mainTitle {
      line-height: 1.1;
      color: $white;
      font-size: 40px;
      font-weight: 500;
      font-family: $hk_bold;
      margin-bottom: 20px;

      @include media-breakpoint-down(md) {
        font-size: 28px;
      }

      @include media-breakpoint-down(sm) {
        font-size: 24px;
      }
    }

    .highlight {
      color: #00ff9c;
      // font-style: italic;
      transition: opacity 0.5s ease-in-out;
    }

    .chainList {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      color: rgba(255, 255, 255, 0.8);
      justify-content: flex-start;
      column-gap: 10px;
      row-gap: 12px;

      .supportedChain {
        display: flex;
        align-items: center;
        padding: 5px 12px;
        border-radius: 17.5px;
        background: rgba(255, 255, 255, 0.12);
        border: 1px solid rgba(255, 255, 255, 0.32);
        position: relative;

        .chainName {
          margin-left: 8px;
          font-size: 14px;

          @include media-breakpoint-down(sm) {
            font-size: 12px;
          }
        }
      }

      .soonBadge {
        position: absolute;
        top: -8px;
        right: -10px;
        background-color: #ff9800;
        color: $white;
        font-size: 10px;
        padding: 2px 6px;
        border-radius: 8px;
        font-weight: bold;

        @include media-breakpoint-down(sm) {
          font-size: 8px;
          padding: 1px 4px;
        }
      }

      @include media-breakpoint-down(sm) {
        justify-content: center;
      }
    }
  }
}
</style>
