<template>
  <view class="person-detail-page" :style="theme">
    <view class="info-list">
      <view class="baseInfo">
        <view class="item">
          <text class="label">黑夜模式</text>
          <evan-switch
            v-model="themeColor"
            @change="setTheme"
          ></evan-switch>
        </view>
        <view class="item" @click="showPickerColor = true">
          <text class="label">文字色彩</text>
        </view>
        <helang-pickerColor
          :isShow="showPickerColor"
          :bottom="0"
          @callback="colorConfirm"
        />
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      showPickerColor: false,
      themeColor: "",
    };
  },
  methods: {
    colorConfirm(color) {
      this.showPickerColor = false;
      this.$store.commit("setCustomTheme", color);
    },
    setTheme(bool) {
      this.$store.commit("setTheme", bool ? "dark" : "light");
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
