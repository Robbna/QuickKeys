<script setup lang="ts">
const props = defineProps<{
  disabled?: boolean;
}>();

const check = defineModel<boolean>("checked", {
  default: false,
});

const emit = defineEmits<{
  (e: "@checked", value: boolean): void;
}>();
</script>
<template>
  <label class="switch">
    <input
      type="checkbox"
      :disabled="props.disabled"
      v-model="check"
      @change="emit('@checked', check)"
    />
    <span class="slider"></span>
  </label>
</template>

<style scoped>
.switch {
  font-size: 17px;
  position: relative;
  display: inline-block;
  width: 4.5em;
  height: 2em;
  transform: scale(0.7);
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  box-shadow: inset 1px 2px 5px 1px rgba(0, 0, 0, 0.329);
  transition: 0.4s;
  border-radius: 30px;

  input:disabled + & {
    cursor: default;
  }
}

.slider:before {
  position: absolute;
  content: "";
  height: 1.4em;
  width: 1.4em;
  border-radius: 20px;
  left: 0.3em;
  bottom: 0.3em;
  background-color: rgb(255, 255, 255);
  transition: 0.4s;
}

.switch input:checked + .slider {
  background-color: #59c76b !important;
}

.switch input:checked + .slider:before {
  transform: translateX(2.5em);
}
</style>
