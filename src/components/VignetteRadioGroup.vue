<template>
  <div
    class="vignette-radio-group-component"
    :id="cid"
    role="radiogroup"
    :aria-labelledby="labelId"
  >
    <span :id="labelId">{{ label }}</span>
    <div class="radiogroup">
      <div
        v-for="(item, idx) in items"
        :key="idx"
        class="vignette-radio"
        role="radio"
        tabindex="0"
        :id="`${cid}_radio_${idx}`"
        :aria-disabled="`${disabled}`"
        :aria-labelledby="`${cid}_radio_${idx}_label`"
        :aria-checked="`${currentValue === item.value}`"
        @focus="onFocus($event, item, idx)"
        @blur="onBlur($event, item, idx)"
      >
        <span :id="`${cid}_radio_${idx}_label`">{{ item.label }}</span>
      </div>
      <!-- <div
        class="child"
        tabindex="0"
        @focus="onFocus(1)"
        :aria-disabled="disabled"
        aria-label="Option 1"
      >
        1
      </div>
      <div
        class="child"
        tabindex="0"
        @focus="onFocus(2)"
        :aria-disabled="disabled"
        aria-label="Option 2"
      >
        2
      </div>
      <div
        class="child"
        tabindex="0"
        @focus="onFocus(3)"
        :aria-disabled="disabled"
        aria-label="Option 3"
      >
        3
      </div>
      <div
        class="child"
        tabindex="0"
        @focus="onFocus(4)"
        :aria-disabled="disabled"
        aria-label="Option 4"
      >
        4
      </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "VignetteSelect",
  props: {
    cid: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      default: () => "Please select a vignette",
    },
    items: {
      type: Array,
      default: () => [
        {
          label: "Option 1",
          value: "option_1",
          url: "https://picsum.photos/200",
        },
        {
          label: "Option 2",
          value: "option_2",
          url: "https://picsum.photos/200",
        },
        {
          label: "Option 3",
          value: "option_3",
          url: "https://picsum.photos/200",
        },
        {
          label: "Option 4",
          value: "option_4",
          url: "https://picsum.photos/200",
        },
      ],
    },
  },
  data() {
    return {
      disabled: true,
      currentValue: null,
    };
  },
  computed: {
    noItems() {
      return this.items.length === 0;
    },
    labelId() {
      return `${this.cid}_label`;
    },
  },
  methods: {
    onFocus(event, item, idx) {
      console.log(`Focusing #${idx}`, { event, item, idx });
      this.currentValue = item.value;
    },
    onBlur(event, item, idx) {
      event.preventDefault();
      console.log(`Blurring #${idx}`, { event, item, idx });
    },
  },
};
</script>

<style lang="css">
.vignette-radio-group-component {
  display: flex;
  flex-direction: column;
}

.vignette-radio-group-component > .radiogroup {
  display: flex;
  flex-wrap: wrap;
}

.vignette-radio-group-component > .radiogroup > .vignette-radio {
  display: flex;
  width: 200px;
  height: 200px;
  background-color: rgba(33, 33, 33, 0.7);
  justify-content: center;
  align-items: center;
  margin: 4px 4px;
  outline: none;
}

.vignette-radio-group-component
  > .radiogroup
  > .vignette-radio[aria-checked="true"] {
  outline: solid blue 2px;
}
</style>