<template>
  <div id="packetList">
    <p class="position"><i class='iconfont'>&#xe8e6;</i>您现在的位置 : 数据应用 > 分组管理 > 分组列表</p>
    <div class="packet_box">
      <table v-loading="loading">
        <tr v-for="(value,index) in teams" :key="index" class="tr_st">
          <td class="teamName">{{value.Name}}</td>
          <td class="number">{{value.Count}}条人才信息</td>
          <td>
            <button class="teamInof" @click="toTeamInfo(value.Id,value.Name)">详情</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    name:"packetList",
    data: function () {
      return {
        teams:[],
        loading:true,
        outerid:sessionStorage.getItem('loginOuterid'),
        accesstoken:sessionStorage.getItem('loginAccesstoken'),
      }
    },
    mounted: function () {
      if(this.$route.path == "/application/packetList"){
        this.$parent.fg1 = true;
      }
      let vm = this;
      vm.$axios({
          method:'post',
          url:window.$g_url.ApiUrl +'/groups?'+ "outerid=" + vm.outerid + "&accesstoken=" + vm.accesstoken,
      })
         .then(function(res){
           vm.loading = false;
           let resdata = res.data;
           if(resdata.code == 0){
             vm.teams = resdata.result;
           }else {
             vm.$message.warning(resdata.message);
           }
         })
         .catch(function(err){
           console.log(err);
         });
    },
    methods:{
      //跳转分组详情
      toTeamInfo: function (id,name) {
        let teamInfo = JSON.stringify({teamId:id,teamName:name})
        sessionStorage.setItem("teamInfo",teamInfo)
        this.$router.push('/application/packetList/teamInfo');
      }
    }
  }
</script>

<style lang="scss" type="text/scss" scoped>
#packetList{
  min-width: 350px;
  .packet_box{
    min-width: 350px;
    table{
      min-width: 350px;
      border-collapse:collapse;
      .tr_st{
        height: 46px;
        line-height: 46px;
        border-bottom:solid 1px #dedede;
        td{
          padding: 0px 30px;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
        .teamName{
          font-size: 16px;
          color: #454545;
        }
        .number{
          font-size: 14px;
          color: #666666;
        }
        .teamInof{
          width: 48px;
          height: 20px;
          line-height: 20px;
          text-align: center;
          background-color: #4ac0f6;
          color: #ffffff;
          margin-top: 13px;
        }
      }
    }
  }
}
</style>

