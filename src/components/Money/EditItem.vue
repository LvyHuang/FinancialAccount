<template>
  <div>
    <label class="notes">
      <Icon name="remark"/>
      <span class="name">{{fieldName}}</span>
      <input type="text" :value="value" @input="onValueChanged($event.target.value)"
             :placeholder="placeholder">
    </label>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';
  import {Component, Prop} from 'vue-property-decorator';

  @Component
  export default class EditItem extends Vue{
    @Prop({required:true}) fieldName!:string;
    @Prop() placeholder!:string;
    @Prop({default: ''}) readonly value!: string;

    onValueChanged(value: string){
      this.$emit('update:value',value);
    }
  }
</script>

<style lang="scss" scoped>
  .notes{
    font-size: 14px;
    padding-left: 16px;
    display: flex;
    align-items: center;
    background: #fff;
    .name{
      padding: 0 12px 0 3px;
    }
    input{
      height: 40px;
      flex-grow: 1;
      background: transparent;
      border: none;
      padding-right: 16px;
    }
  }
</style>