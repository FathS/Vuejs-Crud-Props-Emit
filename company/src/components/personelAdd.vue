<template>
  <div>
    <div class="add-box">
      <div class="form-box">
        <label for="">Name</label>
        <input v-model="personel.Name" type="text" />
      </div>
      <div class="form-box">
        <label for="">Surname</label>
        <input v-model="personel.Surname" type="text" />
      </div>
      <div class="form-box">
        <label for="">Position</label>
        <select name="" id="" v-model="personel.Position">
          <option value="" disabled>Seçiniz</option>
          <option value="Frontend">Frontend</option>
          <option value="Backend">Backend</option>
          <option value="UX/UI">UX/UI</option>
        </select>
      </div>
      <div class="form-box">
        <label for="">Department</label>
        <input v-model="personel.Department" type="text" />
      </div>
      <div class="form-box">
        <label for="">Gender</label>
        <select name="" id="" v-model="personel.Gender">
          <option value="" disabled>Seçiniz</option>
          <option value="Erkek">Erkek</option>
          <option value="Kadın">Kadın</option>
        </select>
      </div>
    </div>
    <button @click="addPersonel()">Ekle</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      personel: {
        Id: 5,
        Name: "",
        Surname: "",
        Age: "",
        Birthday: "",
        Gender: "",
        School: "",
        Position: "",
        Department: "",
        Manager: "",
      },
    };
  },
  methods: {
    addPersonel() {
      this.personel.Id += 1;
      this.$emit("personeladdcomp", this.personel);
    },
  },
};
</script>