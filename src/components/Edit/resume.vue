<template>
  <div id="resume">
    <p class="position"><i class='iconfont'>&#xe8e6;</i>您现在的位置 : 数据加工 > 编辑数据 > 个人简历</p>
    <div class="resumeInfo_box">
      <div class="op">
        <p class='name'>性别:</p>
        <div class="val">
          <el-radio-group v-model="allData.IsMale">
            <el-radio :label="1">男</el-radio>
            <el-radio :label="0">女</el-radio>
          </el-radio-group>
        </div>
      </div>
      <div class="op">
        <p class="name">出生日期:</p>
        <el-date-picker
          type="date"
          v-model='allData.Birthday'
          class="time_box"
          value-format='timestamp'>
        </el-date-picker>
      </div>
      <div class="op">
        <p class="name">国籍:</p>
        <div class="val">
          <el-select
            v-model="allData.Nationality"
            filterable
            allow-create
            class='myel1'
            placeholder="选择或输入留学国籍">
            <el-option
              v-for="item in countrys"
              :key="item"
              :label="item"
              :value="item">
            </el-option>
          </el-select>
        </div>
      </div>
      <div class="op">
        <p class="name">出生地:</p>
        <div class="val">
          <input type="text" placeholder="请输入出生地" v-model='allData.Birthplace' maxlength='20'>
        </div>
      </div>

      <div class="op">
        <p class="name">现居地址:</p>
        <div class="val">
          <input type="text" placeholder="请输入现居住地址" v-model='allData.Residence' maxlength='20'>
        </div>
      </div>

      <div class="op">
        <p class="name">留学国家:</p>
        <div class="val">
          <el-select
            v-model="allData.StudyRegion"
            filterable
            allow-create
            placeholder="选择或输入留学国家">
            <el-option
              v-for="(item,index) in countrys"
              :key="index"
              :label="item"
              :value="item">
            </el-option>
          </el-select>
        </div>
      </div>

      <div class="op">
        <p class="name">毕业院校:</p>
        <div class="val">
          <el-select
            v-model="allData.GraduateSchool"
            filterable
            allow-create
            placeholder="选择或输入毕业院校">
            <el-option
              v-for="(item,index) in colleges"
              :key="index"
              :label="item"
              :value="item">
            </el-option>
          </el-select>
        </div>
      </div>

      <div class="op">
        <p class="name">最高学历:</p>
        <div class="val">
          <el-select
            v-model="allData.HighestDegree"
            filterable
            allow-create
            class="s1">
            <el-option
              v-for="(option,index ) in degrees"
              :key="index"
              :label="option"
              :value="option">
            </el-option>
          </el-select>
        </div>
      </div>

      <div class="op">
        <p class="name">现工作单位:</p>
        <div class="val">
          <input type="text" placeholder="请输入现工作单位" v-model='allData.WorkUnit' maxlength='30'>
        </div>
      </div>

      <div class="op">
        <p class="name">职务:</p>
        <div class="val">
          <input type="text" placeholder="请输入职务" v-model='allData.Position' maxlength='20'>
        </div>
      </div>

      <div class="op">
        <p class="name">通讯地址:</p>
        <div class="val">
          <input type="text" placeholder="请输入地址" v-model='allData.Address' maxlength='30'>
        </div>
      </div>

      <div class="op">
        <p class="name">邮政编码:</p>
        <div class="val">
          <input type="text" placeholder="请输入邮政编码" v-model='allData.Postcode' maxlength='10'>
        </div>
      </div>

      <div class="op">
        <p class="name">联系电话:</p>
        <div class="val">
          <input type="text" placeholder="请输入联系电话" v-model='allData.Phone' maxlength='20'>
        </div>
      </div>

      <div class="op ex">
        <p class="name">海外工作经验:</p>
        <div class="val">
          <el-radio-group v-model="allData.AbroadWorkExp" class='ex1'>
            <el-radio v-for="(option,index) in options6" :label="option.value" class='mb' :key='index'>
              {{option.value}}
            </el-radio>
          </el-radio-group>
        </div>
      </div>

      <div class="op ex">
        <p class="name">是否已经回国工作:</p>
        <div class="val">
          <el-radio-group v-model="allData.WorkHomeStat" class='ex1'>
            <el-radio v-for="(option,index) in options7" :label="option.value" class='mb' :key='index'>
              {{option.value}}
            </el-radio>
          </el-radio-group>
        </div>
      </div>

      <div class="op">
        <p class="name">是否海外创业经历:</p>
        <div class="val">
          <el-radio-group v-model="allData.EverStarupAbroad">
            <el-radio :label="1">是</el-radio>
            <el-radio :label="0">否</el-radio>
          </el-radio-group>
        </div>
      </div>
      <div class="op ex">
        <p class="name">专长优势:</p>
        <div class="val ex">
          <textarea type="text" placeholder='请输入专长优势' class='good' v-model='allData.Advantage'></textarea>
        </div>
      </div>
      <!--<div class="op te">-->
      <!--<p class="name">学位证书:</p>-->
      <!--<div class="val">-->
      <!--<p class="file_box">-->
      <!--<span class="choice_box">-->
      <!--<el-upload-->
      <!--class="upload-demo"-->
      <!--action="https://jsonplaceholder.typicode.com/posts/"-->
      <!--:on-remove="handleRemove"-->
      <!--:multiple="upFile.fg"-->
      <!--:limit="1"-->
      <!--:on-exceed="handleExceed"-->
      <!--:on-change="getfilename1"-->
      <!--:before-upload="beforeAvatarUpload"-->
      <!--:auto-upload="upFile.fg">-->
      <!--<el-button size="small" type="primary" class="btn_choice">选择上传文件</el-button>-->
      <!--</el-upload>-->
      <!--</span>-->
      <!--<span slot="tip" class="el-upload__tip file_name">-->
      <!--{{fileName[0].name}}-->
      <!--</span>-->
      <!--</p>-->
      <!--</div>-->
      <!--</div>-->
      <!--<div class="op te">-->
      <!--<p class="name">个人近照:</p>-->
      <!--<div class="val">-->
      <!--<p class="file_box">-->
      <!--<span class="choice_box">-->
      <!--<el-upload-->
      <!--class="upload-demo"-->
      <!--action="https://jsonplaceholder.typicode.com/posts/"-->
      <!--:on-remove="handleRemove"-->
      <!--:multiple="upFile.fg"-->
      <!--:limit="1"-->
      <!--:on-exceed="handleExceed"-->
      <!--:on-change="getfilename2"-->
      <!--:auto-upload="upFile.fg">-->
      <!--<el-button size="small" type="primary" class="btn_choice">选择上传文件</el-button>-->
      <!--</el-upload>-->
      <!--</span>-->
      <!--<span slot="tip" class="el-upload__tip file_name">-->
      <!--{{fileName[1].name}}-->
      <!--</span>-->
      <!--</p>-->
      <!--</div>-->
      <!--</div>-->
      <!--<div class="op te">-->
      <!--<p class="name">小一寸照:</p>-->
      <!--<div class="val">-->
      <!--<p class="file_box">-->
      <!--<span class="choice_box">-->
      <!--<el-upload-->
      <!--class="upload-demo"-->
      <!--action="https://jsonplaceholder.typicode.com/posts/"-->
      <!--:on-remove="handleRemove"-->
      <!--:multiple="upFile.fg"-->
      <!--:limit="1"-->
      <!--:on-exceed="handleExceed"-->
      <!--:on-change="getfilename3"-->
      <!--:auto-upload="upFile.fg">-->
      <!--<el-button size="small" type="primary" class="btn_choice">选择上传文件</el-button>-->
      <!--</el-upload>-->
      <!--</span>-->
      <!--<span slot="tip" class="el-upload__tip file_name">-->
      <!--{{fileName[2].name}}-->
      <!--</span>-->
      <!--</p>-->
      <!--</div>-->
      <!--</div>-->

      <div class="submit_box">
        <button class="btn_save" @click="subData()">保存</button>
        <button class="toEn" @click="toCh()">英译中</button>
      </div>

    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import commonApi from '../../assets/js/common'
  export default {
    name: 'Resume',
    data: function () {
      return {
        countrys: [],
        colleges: [],
        degrees: [],
        options3: [],
        options6: [
          {value: '刚毕业'},
          {value: '在海外工作1-5年(不含求学阶段)'},
          {value: '在海外工作5年以上(不含求学阶段)'},
        ],
        options7: [
          {value: '长期在国外'},
          {value: '两地往返'},
          {value: '长期在中国'},
        ],
        value: '',
        upFile: {
          fg: false,
        },
        fileName: [
          {
            name: "只能上传jpg/png文件"
          }, {
            name: "只能上传jpg/png文件"
          }, {
            name: "只能上传jpg/png文件"
          }
        ],
        allData: {
          AbroadWorkExp: 0,
          Address: null,
          Advantage: null,
          Birthday: null,
          Birthplace: null,
          EverStarupAbroad: 0,
          GraduateSchool: null,
          HighestDegree: null,
          Img_HighestDegree:null,
          Img_OneInche:null,
          Img_Photo:null,
          IsMale: 1,
          Major:null,
          Nationality: null,
          Phone: null,
          Position: null,
          Postcode: null,
          Residence: null,
          StudyRegion: null,
          UserId:null,
          WorkHomeStat: null,
          WorkUnit: null,
        },
        outerid:sessionStorage.getItem('loginOuterid'),
        accesstoken:sessionStorage.getItem('loginAccesstoken'),
      }
    },
    created: function () {
      if (this.$route.path == "/Edit/resume") {
        this.$parent.fg1 = true;
        this.$parent.fg2 = true;
        this.$parent.fg3 = false;
      }
      commonApi.getAuxiliarydata(this, 'country');
      commonApi.getAuxiliarydata(this, 'college');
      commonApi.getAuxiliarydata(this, 'degree');
      this.getNewData();
    },
    //方法
    methods: {
      //获取初始化数据
      getNewData: function () {
        let vm = this;
        let userid = sessionStorage.getItem('userId');
        if (userid && userid != 0) {
          vm.$axios({
            method: 'post',
            url: window.$g_url.ApiUrl + "/resume?"+ "outerid=" + vm.outerid + "&accesstoken=" + vm.accesstoken,
            data: "userid=" + userid
          })
            .then(function (res) {
              let resDatas = res.data
              if (resDatas.code == 0) {
                if (!resDatas.result) return false;
                vm.allData = resDatas.result;
                if(vm.allData.Birthday){
                  vm.allData.Birthday = vm.allData.Birthday * 1000;
                }else {
                  vm.allData.Birthday = null
                }
              } else {
                vm.$message.error(res.message)
              }
            })
            .catch(function (err) {
              console.log(err);
            })
        };
      },
      //保存上传简历数据
      subData: function () {
        let vm = this;
        let userid = sessionStorage.getItem("userId");
        if (userid && userid != 0) {
          let data = JSON.parse(JSON.stringify(vm.allData));
          data.Birthday = data.Birthday / 1000;
          data.UserId = userid;
          vm.$axios({
            method: 'post',
            url: window.$g_url.ApiUrl + "/setresume?userid=" + userid+ "&outerid=" + vm.outerid + "&accesstoken=" + vm.accesstoken,
            data: JSON.stringify(data)
          })
            .then(function (res) {
              let resDatas = res.data;
              if (resDatas.code == 0) {
                vm.$message.success('保存成功!');
              } else {
                vm.$message.error(resDatas.message);
              }
            })
            .catch(function (err) {
              console.log(err);
            })
        } else {
          vm.$message.warning("请先填写人才信息并保存或到人才列表选择单个人才查看!");
        }
      },
      //二级联动
      handleItemChange: function () {
        let vm = this;
        let val = vm.Birthplace1;
        let i = vm.options2.indexOf(val);
        vm.Birthplace2 = '';
        if (i != -1) {
          vm.options3 = province.arr2[i];
        }
      },
      //英译中
      toCh: function () {
        let vm = this;
        commonApi.toZh(vm,vm.allData);
      }
    }
  }
</script>

<style lang="scss" type="text/scss">
  .resumeInfo_box {
    width: 582px;
    .el-input__inner {
      height: 22px;
      border-radius: 0px;
      line-height: 20px;
      border: solid 1px #53b1dc;
      color: #29a9f5;
    }
    div.op {
      height: 22px;
      width: 100%;
      margin-bottom: 15px;
      p.name {
        width: 196px;
        letter-spacing: 3px;
        font-size: 16px;
        color: #454545;
        float: left;
      }
      div.val {
        width: 310px;
        font-size: 14px;
        float: left;
        select {
          border: solid 1px #53b1dc;
          color: #29a9f5;
          height: 22px;
          line-height: 20px;
        }
        input {
          width: 310px;
          border: solid 1px #53b1dc;
          padding-left: 10px;
          height: 22px;
          line-height: 20px;
        }
        .ex1 {
          height: 80px !important;
          display: flex;
          flex-direction: column;
          justify-content: space-between;
        }
        .s1 {
          width: 148px;
          .el-input__inner {
            width: 148px;
          }
        }
        .s2, .s3 {
          width: 100px;
          float: left;
          .el-input__inner {
            width: 100px;
          }
        }
        .s2 {
          margin-right: 15px;
        }
        .myel1 {
          overflow: hidden;
          .el-input__inner {
            width: 240px;
          }
        }
        .country {
          width: 148px;
          .el-input__inner {
            width: 148px;
          }
        }
      }
      label {
        input {
          margin-right: 5px;
          color: #53b1dc;
        }
      }
    }
    .time_box {
      height: 22px;
      width: 148px;
      .el-input__inner {
        height: 22px;
        width: 148px;
        line-height: 20px;
        border: 1px solid #53b1dc;
        border-radius: 0px;
      }
      span {
        i.el-input__icon {
          line-height: 20px !important;
        }
      }
    }
  }

  .ex {
    height: 80px !important;
  }

  .mb {
    display: block;
    margin-left: 0px !important;
    margin-bottom: 8px;
  }

  .te {
    margin-bottom: 40px !important;
  }

  .good {
    display: block;
    width: 378px;
    height: 120px !important;
    border: solid 1px #53b1dc;
    padding: 5px 0px 0px 5px;
    font-size: 14px;
    color: #454545;
  }

  .file_box {
    width: 278px;
    height: 22px;
    border: solid 1px #53b1dc;
    padding: 0;
    .choice_box {
      display: block;
      width: 100px;
      height: 20px;
      float: left;
      .btn_choice {
        display: block;
        width: 100px;
        height: 20px;
        border: none;
        border-radius: 0px;
        padding: 0;
        color: #53b1dc;
        background-color: #f1f2f6;
        border-right: solid 1px #53b1dc;
        line-height: 22px;
      }
    }
    .file_name {
      display: block;
      width: 174px;
      height: 20px;
      float: right;
      margin: 0px;
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
    }
  }

  .submit_box {
    width: 140px;
    height: 24px;
    margin: 0 auto;
    margin-top: 50px;
    margin-bottom: 60px;
    .btn_save {
      width: 50px;
      height: 24px;
      background-color: #169bd8;
      font-size: 16px;
      text-align: center;
      line-height: 24px;
      color: #fff;
      float: left;
    }
    .toEn {
      width: 66px;
      height: 24px;
      border: solid 1px #999999;
      font-size: 16px;
      color: #545454;
      line-height: 24px;
      background-color: #fff;
      float: right;
    }
  }
</style>

