<template>
  <div class="h-full p-10">
    <div class="row" v-for="index in 9" :key="index">
      <span class="item" :class="'item-' + index + '-' + i"  v-for="i in index" :key="i"></span>
    </div>
  </div>
</template>

<script lang="ts" setup>
</script>

<style lang="less" scoped>
// 定义变量
@cell-padding: 10px;

.row + .row {
  position: relative;
  margin-top: @cell-padding * 3;
}

.item {
  display: inline-block;
  width: 120px;
}

.item + .item {
  margin-left: @cell-padding * 1.5;
}


.calculateCellColor(@row, @column) {
    @isEvenRow: boolean(mod(@row, 2)=0);
    @isEvenColumn: boolean(mod(@column, 2)=0);
    @color: if(@isEvenRow, if(@isEvenColumn, #007bff,  #ff005d), if(@isEvenColumn, #ff005d,  #007bff));
}

@num: range(1, 9, 1);
each(@num, .(@v1){
    each(@num, .(@v2){
        .item-@{v1}-@{v2} {
            &::after{
                padding: @cell-padding;
                border: 2px solid .calculateCellColor(@v1, @v2)[@color];
                @result: @v1 * @v2;
                content: '@{v1} * @{v2} = @{result}';
            }
        }
    })
})
</style>
