<template>
  <div class="detail-wrapper">
    <v-layout row wrap>
      <v-flex xs10 offset-xs1>
        <article class="detail-content text-xs-center">
          <header class="detail-title text-xs-center">
            Detail {{ $route.params.id }}
          </header>
          <router-link
            :to="{
              name: 'detailId',
              params: {
                id: Number($route.params.id) + 1
              }
            }"
          >
            Detail {{ Number($route.params.id) + 1 }}
          </router-link>
          <p>
            Progressive Web Apps are user experiences that have the reach of the
            web, and are: Reliable - Load instantly and never show the
            downasaur, even in uncertain network conditions. Fast - Respond
            quickly to user interactions with silky smooth animations and no
            janky scrolling.
          </p>
          <p>
            Progressive Web Apps are user experiences that have the reach of the
            web, and are: Reliable - Load instantly and never show the
            downasaur, even in uncertain network conditions. Fast - Respond
            quickly to user interactions with silky smooth animations and no
            janky scrolling.
          </p>
          <p>
            Progressive Web Apps are user experiences that have the reach of the
            web, and are: Reliable - Load instantly and never show the
            downasaur, even in uncertain network conditions. Fast - Respond
            quickly to user interactions with silky smooth animations and no
            janky scrolling.
          </p>
          <p>
            Progressive Web Apps are user experiences that have the reach of the
            web, and are: Reliable - Load instantly and never show the
            downasaur, even in uncertain network conditions. Fast - Respond
            quickly to user interactions with silky smooth animations and no
            janky scrolling.
          </p>
          <p>
            Progressive Web Apps are user experiences that have the reach of the
            web, and are: Reliable - Load instantly and never show the
            downasaur, even in uncertain network conditions. Fast - Respond
            quickly to user interactions with silky smooth animations and no
            janky scrolling.
          </p>
          <router-link to="/">back to home</router-link>
        </article>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import axios from "axios";
let state = {
  appHeaderState: {
    show: true,
    title: "Lavas",
    showMenu: false,
    showBack: true,
    showLogo: false,
    actions: [
      {
        icon: "home",
        route: {
          name: "index"
        }
      }
    ]
  }
};

function setState(store) {
  store.dispatch("appShell/appHeader/setAppHeader", state.appHeaderState);
}

export default {
  name: "detailId",
  metaInfo() {
    return {
      title: `Detail ${this.$route.params.id}`,
      titleTemplate: "%s - Lavas",
      meta: [
        { name: "keywords", content: "lavas PWA" },
        {
          name: "description",
          content:
            "基于 Vue 的 PWA 解决方案，帮助开发者快速搭建 PWA 应用，解决接入 PWA 的各种问题"
        }
      ]
    };
  },
  //   async asyncData({store, route}) {
  //       setState(store);
  //       await new Promise((resolve, reject) => {
  //           setTimeout(resolve, 200);
  //       });
  //   },

  async asyncData() {
    // let result = await axios({
    //     method: "get",
    //     url: ` https://www.easy-mock.com/mock/5c792c974cc0df4f4c70b378/list`,
    //     // data: {
    //     //   cityId:"2",
    //     //   token:"677282c2f1b3d718152c4e25ed434bc4"
    //     // },
    //     // headers: {'Authorization': 'APPCODE 5e16e7abc1d845d199ce191751c000c9'},
    // });

    let result = await axios({
      method: "post",
      url: `http://expressq.market.alicloudapi.com/clouds/query/expressQuery`,
      data: {
          "companyCode": 5, // 快递公司编码
          "expressNum": "669824383239" // 快递单号
      },
      headers: {'Authorization': 'APPCODE 5e16e7abc1d845d199ce191751c000c9'},
    //   params: {
    //     type: "top"
    //   }
      // headers: {
      // "Host":"freecityid.market.alicloudapi.com",
      // "X-Ca-Timestamp":"1554988559355",
      // // "gateway_channel":"http",
      // "X-Ca-Request-Mode":"debug",
      // "X-Ca-Key":"26006014",
      // "X-Ca-Stage":"RELEASE",
      // "x-ca-nonce":"3d03d09c-483c-43e5-9d5e-f873a018597e",
      // "Content-Type":"application/x-www-form-urlencoded; charset=utf-8",
      // "Authorization":"APPCODE 5e16e7abc1d845d199ce191751c000c9"}
    });
    // let condition = result.data.query.results.channel.item.condition;

    console.log(result);
    // console.log(
    //   `Weather of Shanghai: ${result.state},${result.data.list[1].id}-----°F`
    // );
    // console.log(`Weather of Shanghai: ${result.code},${result.data}-----°F`);
    // console.log(`Weather of Shanghai: ${condition.t/ext}, ${condition.temp}°F`);
  },
  activated() {
    setState(this.$store);
  }
};
</script>

<style lang="stylus" scoped>
.detail-content {
  font-size: 16px;
  line-height: 30px;
  margin-top: 30px;

  .detail-title {
    margin-bottom: 20px;
    padding: 10px 0;
    font-size: 36px;
    font-weight: bold;
  }
}
</style>
