<template>
  <div style="min-width: 200px" class="relative-pos">
    <label class="w-full" @click="showMessage">{{ label }}
      <span class="count">({{ lengthremaining }})</span>
      <b-icon-chevron-double-right v-if="isHidden"></b-icon-chevron-double-right>
      <b-icon-chevron-double-down v-else></b-icon-chevron-double-down>
    </label>
    <textarea :name="textname" :class="{ 'hidden' : isHidden }" :cols="cols" :rows="rows" class="form-control" v-model="note" @click="notify"></textarea>
    <span :class="{ 'hidden': notificationIsHidden }" class="notification">Nezabudnite uložiť zmeny</span>
  </div>
</template>

<script>
export default {
  name: 'TextInput',
  props: {
    text: String,
    label: String,
    textname: String,
    maxlength: String,
    rows: {
      type: String,
      default: '3'
    },
    cols: {
      type: String,
      default: '24'
    },
  },
  data() {
    return {
      note: this.text,
      isHidden: !this.text.length,
      notificationIsHidden: true
    }
  },
  methods: {
    showMessage: function () {
      this.isHidden = this.isHidden === false
    },
    notify: function () {
      this.notificationIsHidden = this.note !== this.text;
      setTimeout(() => this.notificationIsHidden = true, 5000)
    }
  },
  computed: {
    lengthremaining: function () {
      return this.maxlength - this.note.length
    }
  }
}
</script>

<style scoped>
  .count {
    color: #520606;
  }
  .hidden {
    display: none;
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
    box-shadow: inset 0 1px 1px rgba(0,0,0,.075);
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
  }
</style>
