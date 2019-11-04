<template>
  <div>
    <h3>{{isNew ? '创建' : '编辑'}}课程</h3>
    <ele-form
      :form-data="data"
      :form-desc="fields"
    >

    </ele-form>
  </div>
</template>

<script lang="ts">

  import {Component, Prop, Vue} from "vue-property-decorator";

  @Component({})

  export default class CourseEdit extends Vue {
    @Prop(String) id!: string;

    data = {};
    fields = {
      name: {label: '课程名称', type: 'input'},
      cover: {label: '课程封面', type: 'input'}
    };

    get isNew() {
      return !this.id;
    }

    async fetch() {
      const res = await this.$http.get('courses',);
      this.data = res.data;
    }

    created() {
      // this.fetch();
    }
  }
</script>

<style>

</style>
