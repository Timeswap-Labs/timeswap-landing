<template>
  <section :class="$style.teamPage">
    <div :class="$style.content">
      <div :class="$style.teamList">
        <div :class="$style.teamHeading">
          <h2 :class="$style.mainTitle">Our Team</h2>
          <p :class="$style.mainDescription">
            Our mission is to build the most capital efficient, secure &
            permissionless money market protocol on web 3.0. Come join the
            Timeswap team and help shape the future of DeFi
          </p>
        </div>
        <div
          v-for="(team, index) in teams"
          :key="index"
          :class="$style.teamWrap"
        >
          <div
            :class="$style.teamSingle"
            :style="{
              backgroundImage: `url(${getImgUrl(team.image)})`,
            }"
          >
            <div :class="$style.imgCaption">
              <div :class="$style.nameWrap">
                <h4 :class="$style.name">{{ team.name }}</h4>
                <h4 :class="$style.name">{{ team.lname }}</h4>
              </div>
              <p :class="$style.designation">{{ team.designation }}</p>
            </div>
            <div :class="$style.teamDetails">
              <div :class="$style.info">
                <p :class="$style.teamContent">
                  {{ team.description }}
                </p>
              </div>
              <ul :class="$style.socialLinks">
                <li
                  v-for="(social, socialIndex) in team.socials"
                  v-if="social.link"
                  :key="socialIndex"
                  class="list-inline-item"
                >
                  <a :href="social.link" target="_blank">
                    <img :src="getIconUrl(social.image)" :alt="social.image" />
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div :class="$style.teamWrap">
          <div :class="$style.join_us">Join us</div>
        </div>
      </div>
      <div :class="$style.advisorList">
        <h2 :class="$style.mainTitle">Advisors</h2>
        <div :class="$style.teamWrapList">
          <a
            v-for="(advisor, index) in advisors"
            :key="index"
            :class="$style.teamWrap"
            :href="advisor.link"
            target="_blank"
          >
            <div
              :class="$style.teamSingle"
              :style="{
                backgroundImage: `url(${getImgUrl(advisor.image)})`,
              }"
            >
              <div :class="$style.imgCaption">
                <div :class="$style.nameWrap">
                  <h4 :class="$style.name">{{ advisor.name }}</h4>
                  <h4 :class="$style.name">{{ advisor.lname }}</h4>
                </div>
                <p :class="$style.designation" v-html="advisor.designation" />
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      teams: [
        {
          image: 'ricsson',
          name: 'Ricsson',
          lname: 'Ngo',
          designation: 'Core Contributor',
          description:
            'Previously founder @Einstar. Master in Financial Mathematics from Ateneo de Manila University.',
          socials: [
            {
              link: 'https://twitter.com/TimelordEth',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/ricssontimeswap',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'harshita',
          name: 'Harshita',
          lname: 'Singh',
          designation: 'Core Contributor',
          description:
            'Previously Head of Supply Budgeting and Planning Private Labels @Walmart-India',
          socials: [
            {
              link: 'https://twitter.com/Harshita_125',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/harshita-singh-a1561a79/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'ameeth',
          name: 'Ameeth',
          lname: 'Devadas',
          designation: 'Core Contributor',
          description: 'Previously Head of Product & Technology @Aurigin',
          socials: [
            {
              link: 'https://twitter.com/0x42069x',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/ameeth-devadas-9717679',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'domica',
          name: 'Domica',
          lname: 'Santoso',
          designation: 'Growth Product Manager',
          description: 'DeFi products and investments',
          socials: [
            {
              link: 'https://twitter.com/defi_mimi',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/domica/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'anupama',
          name: 'Anupama',
          lname: 'Singh',
          designation: 'HR & Operations Lead',
          description:
            'Previously worked as an Assistant Professor of Engineering',
          socials: [
            {
              link: 'https://twitter.com/Anupama77220271',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/anupama-singh-855619a1/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'keyur',
          name: 'Keyur',
          lname: 'Shah',
          designation: 'Finance & Legal',
          description: 'Previously VP-Finance & Treasury @Polygon',
          socials: [
            {
              link: 'https://twitter.com/0x_Keyur',
              image: 'twitter',
            },
            {
              link: '',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'krish',
          name: 'Krish Arvind',
          lname: 'Bhatt',
          designation: 'Content Writer',
          description: 'DeFi enthu. Shitposter. Little engineering.',
          socials: [
            {
              link: 'https://twitter.com/0xkrishb',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/krish-bhatt-9776b0234',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'tanishq',
          name: 'Tanishq',
          lname: 'Singh',
          designation: 'Visual Designer',
          description: 'Living between art',
          socials: [
            {
              link: 'https://twitter.com/PerryBerry1325',
              image: 'twitter',
            },
          ],
        },
        {
          image: 'muktanshu',
          name: 'Muktanshu',
          lname: 'Mishra',
          designation: 'Lead Frontend Developer',
          description: 'The FAFO Guy | Music | Games',
          socials: [
            {
              link: 'https://x.com/MuktanshuM',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/muktanshu-mishra-278a85181/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'mohit',
          name: 'Mohit',
          lname: 'Thakkar',
          designation: 'Junior Engineer',
          description:
            'Web3 Dev | Traveler | Content Writer | Crypto & Stocks Trader',
          socials: [
            {
              link: 'https://x.com/mohit_thakkar_',
              image: 'twitter',
            },
            {
              link: 'https://linkedin.com/in/mohit-thakkar-3008',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'tarik',
          name: 'Tarik',
          lname: 'Toromanovic',
          designation: 'Community Manager',
          description: 'DeFi enthusiast',
          socials: [
            {
              link: 'https://x.com/thrayant',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/tarik-toromanovi%C4%87-1883151a2/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'jachin',
          name: 'Jachin Jose',
          lname: 'Victor',
          designation: 'Content Writer',
          description: 'Lawyer and Web3 disciple by dawn. Powerlifter by dusk.',
          socials: [
            {
              link: 'https://x.com/boazlex',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/jachin-victor-3553b1232',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'jerry',
          name: 'Jerry',
          lname: 'Wong',
          designation: 'Full Stack Developer',
          description:
            'Not Degen | Little Dev | Half Trader | Lib Finder | 今日本語専攻中 | Fatboy (try to lose weight)',
          socials: [
            {
              link: 'https://x.com/zetai_moumantai',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/jerry-wong-676b6b284/',
              image: 'linkedin',
            },
          ],
        },
        {
          image: 'soumik',
          name: 'Soumik',
          lname: 'Ghosh',
          designation: 'Senior Backend Developer',
          description:
            'Startup enthusiast with 11 years of experience in system design, scalable architecture, blockchain, and machine learning, backed by strong academics.',
          socials: [
            {
              link: 'https://x.com/GhoshSoumik',
              image: 'twitter',
            },
            {
              link: 'https://www.linkedin.com/in/soumik-ghosh-466b0956/',
              image: 'linkedin',
            },
          ],
        },
      ],
      advisors: [
        {
          image: 'sandeep',
          name: 'Sandeep',
          lname: 'Nailwal',
          designation: 'Founding Advisor<br/>Co-founder, Polygon',
          link: 'https://twitter.com/sandeepnailwal',
        },
        // {
        //   image: 'jaynti',
        //   name: 'Jaynti',
        //   lname: 'Kanani',
        //   designation: 'ex Co-founder, Polygon',
        //   link: 'https://twitter.com/jdkanani',
        // },
      ],
    }
  },
  methods: {
    getImgUrl(team) {
      return require(`../assets/images/${team}.png`)
    },
    getIconUrl(image) {
      return require(`../assets/images/icons/${image}.svg`)
    },
  },
}
</script>

<style lang="scss" module>
.teamPage {
  position: relative;
  width: 100%;
  padding: 100px 160px;
  padding-right: 0;
  display: flex;
  align-items: center;
  flex: 0 0 3300px !important;
  max-width: 3300px !important;
  padding-left: 200px;

  @include media-breakpoint-down(lg) {
    padding-left: 100px;
  }
  @include media-breakpoint-down(md) {
    padding: 80px 50px;
  }
  @include media-breakpoint-down(sm) {
    max-width: 100% !important;
    flex: 0 0 100% !important;
    padding: 60px 24px 40px;
  }
  @include media-breakpoint-down(xs) {
    padding: 40px 24px 0;
  }

  .content {
    width: 100%;
    display: flex;
    align-items: flex-start;

    @include media-breakpoint-down(sm) {
      flex-wrap: wrap;
    }

    .teamList {
      display: grid;
      grid-template-columns: repeat(6, 250px);
      justify-content: start;
      grid-gap: 24px;
      margin-right: 275px;
      grid-auto-flow: column;
      grid-template-rows: repeat(3, 140px);

      @include media-breakpoint-down(sm) {
        width: calc(100% + 16px);
        display: flex;
        flex-wrap: wrap;
        margin: 0 -8px;
        grid-gap: 0px;
        margin-bottom: 50px;
        justify-content: center;
      }

      .teamHeading {
        grid-column-start: 1;
        grid-column-end: 4;

        @include media-breakpoint-down(sm) {
          width: 100%;
          padding: 0 8px;
          text-align: center;
        }
        .mainTitle {
          font-family: $hk_bold;
          line-height: 1.2;
          color: $white;
          margin-bottom: 16px;
        }
        .mainDescription {
          font-size: 14px;
          color: $white;
          opacity: 0.6;
          line-height: 1.5;
          margin-bottom: 0;
          max-width: 900px;

          @include media-breakpoint-down(lg) {
            margin-bottom: 30px;
          }

          @include media-breakpoint-down(xs) {
            max-width: 100%;
          }
        }
      }
      .teamWrap {
        max-width: 250px;
        width: 100%;
        @include media-breakpoint-down(sm) {
          margin-bottom: 20px;
          padding: 0 8px;
          max-width: 266px;
        }
        // Founder Cards
        &:nth-child(2),
        &:nth-child(3),
        &:nth-child(4) {
          grid-row-start: 2;
          grid-row-end: 4;
          .teamSingle {
            height: 304px !important;
            max-width: auto !important;
            align-items: flex-end !important;
            &.teamContent {
              font-size: 16px !important;
            }
          }
        }
        .teamSingle {
          border-radius: 10px;
          position: relative;
          overflow: hidden;
          display: flex;
          align-items: center;
          height: 140px;
          background-size: cover;
          width: 250px;
          background-position: center;
          .imgCaption {
            width: 100%;
            padding: 16px 25px;
            max-width: 70%;

            @include media-breakpoint-down(sm) {
              padding: 15px;
            }

            .nameWrap {
              margin-bottom: 10px;

              @include media-breakpoint-down(xs) {
                margin-bottom: 1px;
              }

              .name {
                font-size: 16px;
                font-family: $hk_bold;
                line-height: 1.3;
                color: $white;
                padding-right: 14px;
                margin-bottom: 0;
                @include media-breakpoint-down(xs) {
                  font-size: 14px;
                  margin-bottom: 1px;
                }
              }
            }
            .designation {
              font-size: 14px;
              line-height: 1.5;
              color: $white;
              opacity: 0.6;
              margin-bottom: 0;
              @include media-breakpoint-down(xs) {
                font-size: 13px;
              }
            }
          }
          .teamDetails {
            position: absolute;
            top: 0;
            width: 100%;
            height: 100%;
            left: 0;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 20px;
            background: $corn-flower;
            opacity: 0;
            pointer-events: none;
            transition: all 0.5s;
            transform: translateY(30px);
            border-radius: 10px;
            @include media-breakpoint-down(sm) {
              padding: 14px;
            }
            .info {
              .teamContent {
                font-size: 12px;
                color: $gray-900;
                margin: 0;
              }
            }
            .socialLinks {
              display: flex;
              width: 100%;
              justify-content: flex-start;
              margin: 0;
              padding: 0;
              list-style: none;
              li {
                margin-right: 4px;
              }
            }
          }
          &:hover {
            .teamDetails {
              opacity: 1;
              pointer-events: auto;
              transform: translateY(0);
            }
          }
        }
        .join_us {
          width: 100%;
          color: $white;
          height: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
          font-size: 20px;
          background: $ldark-navy;
          border-radius: 10px;
          cursor: pointer;
          display: none;
          @include media-breakpoint-down(md) {
            height: 270px;
          }
          @include media-breakpoint-down(xs) {
            height: 207px;
            font-size: 13px;
          }
        }
      }
    }

    .advisorList {
      max-width: 314px;
      width: 100%;

      @include media-breakpoint-down(sm) {
        width: 100%;
        max-width: 100%;
        margin-bottom: 50px;
      }
      .mainTitle {
        font-family: $hk_bold;
        line-height: 1.2;
        color: $white;
        margin-bottom: 50px;
        @include media-breakpoint-down(sm) {
          text-align: center;
        }
      }
      .teamWrapList {
        @include media-breakpoint-down(sm) {
          display: flex;
          flex-wrap: wrap;
          margin: 0 -8px;
          justify-content: center;
        }
        .teamWrap {
          max-width: 314px;
          width: 100%;
          margin-bottom: 20px;
          display: inline-block;
          @include media-breakpoint-down(sm) {
            margin-bottom: 20px;
            max-width: 266px;
            padding: 0 8px;
          }
          .teamSingle {
            border-radius: 10px;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            height: 175px;
            background-size: cover;
            width: 100%;
            background-position: center;

            @include media-breakpoint-down(sm) {
              height: 140px;
            }

            .imgCaption {
              width: 100%;
              padding: 16px 25px;
              max-width: 70%;

              @include media-breakpoint-down(sm) {
                padding: 15px;
              }

              .nameWrap {
                margin-bottom: 10px;

                @include media-breakpoint-down(xs) {
                  margin-bottom: 1px;
                }

                .name {
                  font-size: 16px;
                  font-family: $hk_bold;
                  line-height: 1.3;
                  color: $white;
                  padding-right: 14px;
                  margin-bottom: 0;

                  @include media-breakpoint-down(md) {
                    font-size: 15px;
                  }

                  @include media-breakpoint-down(xs) {
                    font-size: 13px;
                  }
                }
              }
              .designation {
                font-size: 14px;
                line-height: 1.5;
                color: $white;
                opacity: 0.6;
                margin-bottom: 0;

                @include media-breakpoint-down(md) {
                  font-size: 15px;
                }

                @include media-breakpoint-down(xs) {
                  font-size: 12px;
                }
              }
            }
            .teamDetails {
              position: absolute;
              top: 0;
              width: 100%;
              height: 100%;
              left: 0;
              display: flex;
              flex-direction: column;
              justify-content: space-between;
              padding: 20px;
              background: $corn-flower;
              opacity: 0;
              pointer-events: none;
              transition: all 0.5s;
              transform: translateY(30px);
              border-radius: 10px;

              @include media-breakpoint-down(md) {
                padding: 15px;
              }

              .info {
                .name {
                  font-size: 16px;
                  font-family: $hk_bold;
                  line-height: 1.5;
                  color: $gray-900;
                  margin-bottom: 0;

                  @include media-breakpoint-down(md) {
                    font-size: 15px;
                  }

                  @include media-breakpoint-down(sm) {
                    font-size: 13px;
                  }
                }
                .designation {
                  font-size: 16px;
                  line-height: 1.5;
                  color: $gray-900;
                  margin-bottom: 16px;

                  @include media-breakpoint-down(md) {
                    font-size: 15px;
                  }

                  @include media-breakpoint-down(sm) {
                    font-size: 12px;
                    margin-bottom: 8px;
                  }
                }
                .teamContent {
                  font-size: 12px;
                  color: $gray-900;
                  margin: 0;
                  @include media-breakpoint-down(sm) {
                    font-size: 13px;
                    line-height: 1.4;
                  }
                }
              }
              .socialLinks {
                display: flex;
                width: 100%;
                justify-content: flex-start;
                margin: 0;
                padding: 0;
                list-style: none;
                li {
                  margin-right: 4px;
                }
              }
            }
            &:hover {
              .teamDetails {
                opacity: 1;
                pointer-events: auto;
                transform: translateY(0);
              }
            }
          }
          .join_us {
            width: 100%;
            color: $white;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            background: $ldark-navy;
            border-radius: 10px;
            cursor: pointer;
            display: none;

            @include media-breakpoint-down(md) {
              height: 270px;
            }

            @include media-breakpoint-down(xs) {
              height: 207px;
              font-size: 13px;
            }
          }
        }
      }
    }
  }
}
</style>
