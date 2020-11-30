<template>
  <div>
    <div class="container">
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Surname</th>
            <th>Position</th>
            <th>Department</th>
            <th>Manager</th>
            <th>Edit</th>
            <th>Delete</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="personel in personelList" :key="personel.id">
            <td>{{ personel.Name }}</td>
            <td>{{ personel.Surname }}</td>
            <td>{{ personel.Position }}</td>
            <td>{{ personel.Department }}</td>
            <td>{{ personel.Manager }}</td>
            <td @click="getDetail(personel)">Edit</td>
            <td>Delete</td>
          </tr>
          <Popup
            v-if="togglePopup"
            :gender="Pgender"
            :id="PId"
            :personel="Ppersonel"
            @closePopup="togglePopup = $event"
          />
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Popup from "./personelDetail";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      personelList: [
        {
          id: 1,
          Name: "Fatih",
          Surname: "Şengül",
          Age: 25,
          Birthday: 1995,
          Gender: "Erkek",
          School: "Lisans",
          Position: "FrontEnd Developer",
          Department: "Tasarım Atölyesi",
          Manager: "Will Smith",
        },
        {
          id: 2,
          Name: "Joe",
          Surname: "Dohn",
          Age: 40,
          Birthday: 1980,
          Gender: "Erkek",
          School: "Lisans",
          Position: "Backend Developer",
          Department: "Tasarım Atölyesi",
          Manager: "Will Smith",
        },
        {
          id: 3,
          Name: "Mike",
          Surname: "Tyson",
          Age: 55,
          Birthday: 1965,
          Gender: "Erkek",
          School: "Yüksek Lisans",
          Position: "UX-UI",
          Department: "Tasarım Atölyesi",
          Manager: "Will Smith",
        },
        {
          id: 4,
          Name: "Ayşe",
          Surname: "Ayşen",
          Age: 25,
          Birthday: 1995,
          Gender: "Kadın",
          School: "Lisans",
          Position: "FrontEnd Developer",
          Department: "Tasarım Atölyesi",
          Manager: "Orkun Yeşim",
        },
        {
          id: 5,
          Name: "Fatih",
          Surname: "Şengül",
          Age: 25,
          Birthday: 1995,
          Gender: "Erkek",
          School: "Lisans",
          Position: "Full Stack",
          Department: "Tasarım Atölyesi",
          Manager: "Orkun Yeşim",
        },
      ],
      togglePopup: false,
      PId: "",
      Pgender: "",
      Ppersonel: {},
    };
  },
  methods: {
    getDetail(item) {
      //2 Çeşit yol var. İsterseniz sadece istediğiniz verileri gönderin...
      this.togglePopup = !this.togglePopup; //Popup Açılıp Kapanması için
      this.Pgender = item.Gender;
      this.PId = item.id;
      //2 Çeşit yol bitişi. İsterseniz sadece istediğiniz verileri gönderin...

      //İsterseniz direk objeyi gönderin
      this.Ppersonel = item;
    },
  },
  components: {
    Popup,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.container {
  position: relative;
  width: 96%;
  max-width: 1600px;
  margin: 0 auto;
  padding: 0;
}
table {
  position: relative;
  width: 100%;
  border-collapse: collapse;
  margin-top: 100px;
}
table thead tr th,
table tbody tr td {
  padding: 10px;
  border-bottom: 1px solid #d3d3d3;
  color: #000000;
  cursor: pointer;
}
table tbody tr:nth-child(even) {
  background-color: rgb(235, 235, 235);
}
table tbody tr:hover {
  background-color: rgb(206, 206, 206);
  transition: all 0.4s ease;
}
</style>
