<template>
  <el-row :gutter="40" class="panel-group">
    <el-col :xs="16" :sm="16" :lg="8" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('newVisitis')">
        <div class="card-panel-icon-wrapper icon-people">
          <svg-icon icon-class="peoples" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">在职员工</div>
          <count-to :start-val="0" :end-val="clerkCount" class="card-panel-num" />
        </div>
      </div>
    </el-col>
    <!-- <el-col :xs="12" :sm="12" :lg="6" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('messages')">
        <div class="card-panel-icon-wrapper icon-message">
          <svg-icon icon-class="message" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">通知</div>
          <count-to
            :start-val="0"
            :end-val="annCount"
            class="card-panel-num"
          />
        </div>
      </div>
    </el-col> -->
    <el-col :xs="16" :sm="16" :lg="8" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('purchases')">
        <div class="card-panel-icon-wrapper icon-money">
          <svg-icon
            icon-class="documentation
"
            class-name="card-panel-icon"
          />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">考勤信息</div>
          <count-to
            :start-val="0"
            :end-val="attendanceCount"
            class="card-panel-num"
          />
        </div>
      </div>
    </el-col>
    <el-col :xs="16" :sm="16" :lg="8" class="card-panel-col">
      <div class="card-panel" @click="handleSetLineChartData('shoppings')">
        <div class="card-panel-icon-wrapper icon-shopping">
          <svg-icon icon-class="clipboard" class-name="card-panel-icon" />
        </div>
        <div class="card-panel-description">
          <div class="card-panel-text">奖惩信息</div>
          <count-to
            :start-val="0"
            :end-val="rewardsPunishmentsCount"
            class="card-panel-num"
          />
        </div>
      </div>
    </el-col>
  </el-row>
</template>

<script>
import CountTo from "vue-count-to";
export default {
  data() {
    return {
      clerkCount: 0,
      annCount: 0,
      attendanceCount: 0,
      rewardsPunishmentsCount: 0
    };
  },
  created(){
    ann.numInfo().then(response => {
      this.clerkCount = response.data.clerkCount;
      this.annCount = response.data.annCount;
      this.attendanceCount = response.data.attendanceCount;
      this.rewardsPunishmentsCount = response.data.rewardsPunishmentsCount;
    })
  },
  components: {
    CountTo,
  },
  methods: {
    handleSetLineChartData(type) {
      this.$emit("handleSetLineChartData", type);
    },
  },
};
</script>

<style lang="scss" scoped>
.panel-group {
  margin-top: 18px;

  .card-panel-col {
    margin-bottom: 32px;
  }

  .card-panel {
    height: 108px;
    cursor: pointer;
    font-size: 12px;
    position: relative;
    overflow: hidden;
    color: #666;
    background: #fff;
    box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.05);
    border-color: rgba(0, 0, 0, 0.05);

    &:hover {
      .card-panel-icon-wrapper {
        color: #fff;
      }

      .icon-people {
        background: #40c9c6;
      }

      .icon-message {
        background: #36a3f7;
      }

      .icon-money {
        background: #f4516c;
      }

      .icon-shopping {
        background: #34bfa3;
      }
    }

    .icon-people {
      color: #40c9c6;
    }

    .icon-message {
      color: #36a3f7;
    }

    .icon-money {
      color: #f4516c;
    }

    .icon-shopping {
      color: #34bfa3;
    }

    .card-panel-icon-wrapper {
      float: left;
      margin: 14px 0 0 14px;
      padding: 16px;
      transition: all 0.38s ease-out;
      border-radius: 6px;
    }

    .card-panel-icon {
      float: left;
      font-size: 48px;
    }

    .card-panel-description {
      float: right;
      font-weight: bold;
      margin: 26px;
      margin-left: 0px;

      .card-panel-text {
        line-height: 18px;
        color: rgba(0, 0, 0, 0.45);
        font-size: 16px;
        margin-bottom: 12px;
      }

      .card-panel-num {
        font-size: 20px;
      }
    }
  }
}

@media (max-width: 550px) {
  .card-panel-description {
    display: none;
  }

  .card-panel-icon-wrapper {
    float: none !important;
    width: 100%;
    height: 100%;
    margin: 0 !important;

    .svg-icon {
      display: block;
      margin: 14px auto !important;
      float: none !important;
    }
  }
}
</style>
