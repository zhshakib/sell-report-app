<template>
  <div class="q-pa-md full-width">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        v-model="name"
        label="Item Name"
        lazy-rules
        :rules="[
          val => (val && val.length > 0) || 'নাম লেখোস নাই ক্যান মাদারচোদ'
        ]"
      />

      <q-input
        type="number"
        v-model="age"
        label="Enter Price"
        lazy-rules
        :rules="[
          val => (val !== null && val !== '') || 'টাকা লেখবে কি তোর নানায় ?',
          val => (val > 0 && val < 100) || 'Please type a real age'
        ]"
      />

      <q-toggle
        v-model="accept"
        :label="accept ? 'এইবার ঠিক আছে! 🌝' : 'বাকি চোদাও ? 😠'"
        class="text-secondary"
      />

      <div class="text-dark">
        <q-btn label="Submit" type="submit" color="secondary" />
        <q-btn label="Reset" type="reset" color="primary" class="q-ml-sm" />
      </div>
    </q-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: null,
      age: null,
      accept: false
    };
  },

  methods: {
    onSubmit() {
      if (this.accept !== true) {
        this.$q.notify({
          color: "secondary",
          textColor: "white",
          icon: "warning",
          message: "You need to accept the license and terms first"
        });
      } else {
        this.$q.notify({
          color: "green-4",
          textColor: "white",
          icon: "cloud_done",
          message: "Submitted"
        });
      }
    },

    onReset() {
      this.name = null;
      this.age = null;
      this.accept = false;
    }
  }
};
</script>
