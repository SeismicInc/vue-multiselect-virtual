<template>
    <li class="multiselect__element"
        style="box-sizing: border-box">
                <span
                        v-if="!(option && (option.$isLabel || option.$isDisabled))"
                        :class="className(index, option)"
                        @click.stop="select(option)"
                        @mouseenter.self="pointerSet(index)"
                        :data-select="option && option.isTag ? tagPlaceholder : selectLabelText"
                        :data-selected="selectedLabelText"
                        :data-deselect="deselectLabelText"
                        class="multiselect__option">
                    <slot name="option" :option="option" :search="search">
                      <span>{{ getOptionLabel(option) }}</span>
                    </slot>
                </span>
        <span
                v-if="option && (option.$isLabel || option.$isDisabled)"
                :data-select="groupSelect && selectGroupLabelText"
                :data-deselect="groupSelect && deselectGroupLabelText"
                :class="groupHighlight(index, option)"
                @mouseenter.self="groupSelect && pointerSet(index)"
                @mousedown.prevent="selectGroup(option)"
                class="multiselect__option">
                    <slot name="option" :option="option" :search="search">
                      <span>{{ getOptionLabel(option) }}</span>
                    </slot>
                </span>
    </li>
</template>

<script>
  export default {
    name: 'ScrollItem',
    props: {
      'index': Number,
      'option': Object,
      'className': Function,
      'select': Function,
      'pointerSet': Function,
      selectLabelText: String,
      selectedLabelText: String,
      deselectLabelText: String,
      getOptionLabel: Function,
      selectGroupLabelText: String,
      deselectGroupLabelText: String,
      groupHighlight: Function,
      selectGroup: Function,
      search: String
    },
    mounted () {
      window.optionHighlight = this.optionHighlight
    }
  }
</script>

<style scoped>

</style>
