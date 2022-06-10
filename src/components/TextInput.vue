<template>
  <div
    style="min-width: 200px"
    class="relative"
  >
    <label
      class="flex items-center"
      @click="showMessage"
    >{{ label }}
      <span class="count">({{ remainingLength }})</span>

      <svg
        v-if="isHidden"
        xmlns="http://www.w3.org/2000/svg"
        width="28"
        height="28"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="#2c3e50"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path
          stroke="none"
          d="M0 0h24v24H0z"
          fill="none"
        />
        <polyline points="6 9 12 15 18 9" />
      </svg>

      <svg
        v-else
        xmlns="http://www.w3.org/2000/svg"
        width="28"
        height="28"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="#2c3e50"
        fill="none"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        <path
          stroke="none"
          d="M0 0h24v24H0z"
          fill="none"
        />
        <polyline points="6 15 12 9 18 15" />
      </svg>
    </label>
    <textarea
      v-model="note"
      :name="textname"
      :class="{ 'hidden' : isHidden }"
      :cols="cols"
      :rows="rows"
      class="form-control"
      @click="notify"
    />
    <span
      :class="{ 'hidden': notificationIsHidden }"
      class="notification"
    >Dont forget to save changes</span>
  </div>
</template>

<script setup>

import {computed, ref} from "vue";

const props = defineProps({
    text: {type: String,default:''},
    label: {type: String,default:'Label'},
    textname: {type: String,default:''},
    maxlength: {type: Number,default:500},
    rows: {
        type: String,
        default: '3'
    },
    cols: {
        type: String,
        default: '24'
    },
})

const note = ref(props.text);
const isHidden = ref(!props.text.length);
const notificationIsHidden = ref(true);

const remainingLength = computed(() => {
    return props.maxlength - note.value.length
})

function showMessage() {
    isHidden.value = isHidden.value === false
}

function notify() {
    notificationIsHidden.value = note.value !== props.text;
    setTimeout(() => notificationIsHidden.value = true, 5000)
}
</script>

<style scoped>
.count {
    color: #520606;
}

.hidden {
    display: none;
}

.flex {
    display: flex;
}

.items-center {
    align-items: center;
}

.notification {
    position: absolute;
    bottom: 5px;
    left: 5px;
    color: #520606;
    background-color: #f2dede;
    border-color: #ebccd1;
    padding: 1px 5px;
    border-radius: 3px;
    font-size: 0.8rem;
}

.form-control {
    box-sizing: border-box;
    width: 100%;
    padding: 4px 8px;
    font-size: 1em;
    line-height: 1.42857143;
    color: #555;
    background-color: #fff;
    background-image: none;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-shadow: inset 0 1px 1px rgba(0, 0, 0, .075);
    transition: border-color .15s ease-in-out, box-shadow .15s ease-in-out;
}

.relative {
    position: relative;
}
</style>
