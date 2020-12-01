<template>
  <div>
    <div class="container">
      <div class="detail-popup">
        <strong>{{ personel.Name }} {{ personel.Surname }} ait bilgiler</strong
        ><br /><br />
        <p>Id: {{ id }}</p>
        <p>Id: {{ personel.Id }}</p>
        <p>Yaş:{{ personel.Age }}</p>
        <p>D.Tarihi:{{ personel.Birthday }}</p>
        <p>Okul:{{ personel.School }}</p>
        <p>Cinsiyet:{{ gender }}</p>
        <p>Cinsiyet:{{ personel.Gender }}</p>
        <input type="text" v-model="personel.Gender" name="" id="" />
        <div class="button" @click="closePopup()">Close</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
    },
    age: {
      type: String,
      required: true,
    },
    birthday: {
      type: Number,
    },
    school: {
      type: String,
    },
    gender: {
      type: String,
    },
    personel: {
      type: Object,
    },
  },
  data() {
    return {};
  },
  methods: {
    closePopup() {
      this.$emit("closePopup", false);
    },
  },
};
</script>
<style>
.detail-popup {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 50%;
  height: 500px;
  padding: 50px;
  background-color: #ffffff;
  border: 1px solid gray;
  border-radius: 15px;
  text-align: left;
  z-index: 5;
}
.button {
  position: absolute;
  bottom: 10px;
  right: 10px;
  cursor: pointer;
  font-weight: bold;
}
</style>