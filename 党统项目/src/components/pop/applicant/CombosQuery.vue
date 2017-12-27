<!--党组织管理/查询统计/组合查询弹窗-->
<template>
  <div class="CombinationQuery">
    <Modal
      v-model="modal1"
      title="组合查询"
      width="950"
      :loading="loading"
      :mask-closable=false
      :closable=false
      class-name="max-height"
      @on-ok=""
      @on-cancel="cancel">
      <Form ref="CombinationQueryForm" :model="CombinationQueryForm"  inline label-position="top">
        <Row>
          <Col span="20">
            <p class="bold">条件设置</p>
            <Row style="margin-top: 20px">
              <Col span="6">
                <FormItem label="选择信息集：" prop="major"  style="width: 95%;">
                  <Input v-model="CombinationQueryForm.major" placeholder="请输入"></Input>
                </FormItem>
              </Col>
              <Col span="6">
              <FormItem label="选择信息集：" prop="major"  style="width: 95%;">
                <Input v-model="CombinationQueryForm.major" placeholder="请输入"></Input>
              </FormItem>
              </Col> <Col span="6">
              <FormItem label="操作符：" prop="major" style="width: 95%;">
                <Input v-model="CombinationQueryForm.major" placeholder="请输入"></Input>
              </FormItem>
              </Col>
              <Col span="6">
              <FormItem label="查询值：" prop="major" style="width: 95%;">
                <Input v-model="CombinationQueryForm.major" placeholder="请输入"></Input>
              </FormItem>
              </Col>
            </Row>
            <Row>
              <Button class="mr-5">并且</Button>
              <Button class="mr-5">或者</Button>
              <Button class="mr-5">(+</Button>
              <Button class="mr-5">+)</Button>
              <Button class="mr-5">(-</Button>
              <Button class="mr-5">-)</Button>
              <Button class="mr-5 fr">添加</Button>
            </Row>
          </Col>
        </Row>
        <Row>
          <Col span="20">
            <div class="box-wrap"></div>
            <Row style="text-align: right;margin-top: 10px">
              <Button type="error" size="large">查询</Button>
              <Button type="warning" size="large" class="ml-10">保存为固定条件</Button>
            </Row>
          </Col>
          <Col span="4">
            <Row style="text-align: center;margin-top: 35px">
              <Button class="mb10 w100">上移</Button>
              <Button class="mb10 w100">下移</Button>
              <Button class="mb10 w100">删除</Button>
              <Button class="mb10 w100">全删</Button>
            </Row>
          </Col>
        </Row>
        <Row>
          <Col span="20">
            <p class="bold">固定查询条件</p>
            <Table border :columns="columns1" :data="data1"></Table>
          </Col>
          <Col span="4">
            <Row style="text-align: center;margin-top: 30px">
              <Button class="mb10 w100">删除条件</Button>
              <Button class="mb10 w100">导出条件</Button>
              <Button class="mb10 w100">导入条件</Button>
            </Row>
          </Col>
        </Row>
      </Form>
    </Modal>
  </div>
</template>
<script>
  export default {
    name:'CombinationQuery',
    data () {
      return {
        modal1: true,//是否显示弹窗
        loading: true,
        CombinationQueryForm: {  //form的绑定
          revoketDate:'',//撤销时间
        },
        ruleValidate: {
          revoketDate: [
            {required: true,type:'date', message: '撤销日期不能为空', trigger: 'change'}
          ],
        },
        columns1: [
          {
            title: '固定条件类型',
            key: 'fixedType'
          },
          {
            title: '定义类别',
            key: 'definedCategory'
          },
        ],
        data1: [
          {
            fixedType: '系统条件一',
            definedCategory: '系统定义',
          },
          {
            fixedType: '系统条件二',
            definedCategory: '自定义',
          },
        ]
      }
    },

    methods: {
      handleSubmit(name) {
        this.$refs[name].validate((valid) => {
          if (valid) {
            this.$Message.success('提交成功!');
            this.modal1=false;
            this.$router.go(-1)
          } else {
            this.loading=false;
        this.$Message.error('表单验证失败!');
        setTimeout(() => {
          this.loading=true;
      }, 20);
      }
      })
      },
      cancel () {
        this.$Message.info('点击了取消');
        this.$router.go(-1)
      }
    }
  }
</script>
<style>
  .max-height .ivu-modal-body{
    max-height: 500px;
    overflow-y: auto;
    overflow-x: hidden;
  }
  .box-wrap{
    width: 100%;
    height: 180px;
    border: 1px solid #dddee1;
    -webkit-border-radius: 2px;
    -moz-border-radius: 2px;
    border-radius: 2px;;
    margin-top: 20px;
  }
  .bold{
    font-weight: bold;
    font-size: 14px;
  }
  .fr{
    float: right;
  }
  .mr-5{
    margin-right: 10px;
    padding-left:25px ;
    padding-right:25px ;
  }
  .ml-10{
    margin-left: 10px;
  }
  .mb10{
    margin-bottom: 10px;
  }
 .w100{
   width: 100px;
 }
</style>
