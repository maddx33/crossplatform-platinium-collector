<template>
  <div class="home">
    <InputView
      v-if="platforms.length < 1"
      @platforms="
        (v) => {
          this.platforms = v;
        }
      "
    />
    <AlbumView v-if="platforms.length > 0" :platforms="platforms" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import InputField from "@/components/InputField.vue";
import LoadingIndicator from "@/components/LoadingIndicator.vue";
import PlatformFetch from "@/components/PlatformFetch.vue";
import { Platform, PlatiniumTrophy } from "@/types/types";
import TrophiesAlbum from "@/components/TrophiesAlbum.vue";
import PlatformInfo from "@/components/PlatformInfo.vue";
import InputView from "@/views/InputView.vue";
import AlbumView from "@/views/AlbumView.vue";

@Options({
  components: {
    AlbumView,
    InputView,
    PlatformInfo,
    TrophiesAlbum,
    PlatformFetch,
    LoadingIndicator,
    InputField,
  },
})
export default class HomeView extends Vue {
  platforms: Platform[] = [];
}
</script>

<style lang="scss" scoped>
@import "src/breakpoints.scss";

.home {
  width: 100%;
  height: calc(100% - 100px);
  display: flex;
  flex-direction: column;
  padding: 50px;
}

.album-wrapper {
  position: absolute;
  transform: translate(-50%, 0);
  left: 50%;
  bottom: 10%;
}

.trophies-album {
  //position: absolute;
  //top: 0;
  //left: 0;
}

.title {
  color: white;
  @include respond-to("large") {
    font-size: 16px;
  }
}

.platform-info-wrapper {
  display: flex;
  width: 100%;
  justify-content: space-evenly;
  align-items: center;
}
</style>
