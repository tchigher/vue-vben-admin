<script lang="tsx">
  import { defineComponent } from 'compatible-vue';
  import { Alert } from 'ant-design-vue';
  import { Description, DescItem, useDescription } from '@/components/description/index';
  const mockData = {
    username: 'test',
    nickName: 'VB',
    age: 25,
    phone: '15695909xxx',
    email: '190848757@qq.com',
    addr: '厦门市思明区观日路18号',
    sex: '男',
    certy: '3504256199xxxxxxxxx',
    tag: 'orange',
  };
  const schema: DescItem[] = [
    {
      field: 'username',
      label: '用户名',
    },
    {
      field: 'nickName',
      label: '昵称',
    },
    {
      field: 'phone',
      label: '联系电话',
    },
    {
      field: 'email',
      label: '邮箱',
    },
    {
      field: 'addr',
      label: '地址',
      // show: () => {
      //   return false;
      // },
    },
  ];
  export default defineComponent({
    name: 'DescDemo',
    setup() {
      const [register] = useDescription({
        title: '无边框示例',
        bordered: false,
        data: mockData,
        schema: schema,
      });

      return () => (
        <div class="p-4">
          <Alert message="二次封装Desc组件，提供useDescription 函数方便调用" />
          <Description
            class="m-2"
            title="基础示例"
            collapseOptions={{
              canExpand: true,
              helpMessage: 'help me',
            }}
            column={3}
            data={mockData}
            schema={schema}
          />

          <Description
            class="m-2"
            title="垂直示例"
            layout="vertical"
            column={2}
            data={mockData}
            schema={schema}
          />
          <Description onRegister={register} class="m-2" />
        </div>
      );
    },
  });
</script>
