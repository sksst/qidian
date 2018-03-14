<template>
  <div class="btn-group">
    <h3 v-for="(tab,index) in tabs"
        :key="index"
        class="btn-group-cell"
        role="tab"
        :aria-selected="index === selectIndex"
        @click.stop="select(index)"
    >
      <a href="javascript:" :class="selectClass(index)" :data-index="index">{{tab}}</a>
    </h3>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    name: 'module-tab',
    data () {
      return {
        selectIndex: 0
      }
    },
    props: {
      tabs: {
        type: Array,
        default: []
      }
    },
    computed: {
    },
    methods: {
      selectClass (index) {
        if (this.selectIndex === index) {
          return 'btn-tab active'
        }
        return 'btn-tab'
      },
      select (index) {
        this.selectIndex = index
        this.$emit('select', index)
      }
    }
  }
</script>

<style scoped lang="stylus">
  .btn-group
    display: table
    width: 100%
    margin-right: auto
    margin-left: auto
    table-layout: fixed
    .btn-group-cell
      font-size: 100%
      font-weight: 400
      display: table-cell
      .btn-tab
        font-size: .8125rem
        line-height: 1.6875rem
        display: block
        padding: 0 .5rem
        text-align: center
        color: #ed424b
        border: 1px solid #ed424b
      .active
        color: #ffffff
        background-color: #ed424b
      &:first-child
        .btn-tab
          border-radius: 4px 0 0 4px
      &:last-child
        .btn-tab
          border-radius: 0 4px 4px 0
</style>
