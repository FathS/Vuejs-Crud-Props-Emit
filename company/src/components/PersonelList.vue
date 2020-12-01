<template>
  <div>
    <div class="container">
      <div class="row">
        <p style="cursor: pointer" @click="addPerson = !addPerson">
          Personel Ekle / Vazgeç
        </p>
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
            <tr v-for="(personel, index) in personelList" :key="personel.id">
              <td>{{ personel.Name }}</td>
              <td>{{ personel.Surname }}</td>
              <td>{{ personel.Position }}</td>
              <td>{{ personel.Department }}</td>
              <td>{{ personel.Manager }}</td>
              <td @click="getDetail(personel)">Edit</td>
              <td @click="deletePersonel(index)">Delete</td>
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
        <addPersonel @personeladdcomp="AddPersonel($event)" v-if="addPerson" />
      </div>
    </div>
  </div>
</template>

<script>
import Popup from "./personelDetail";
import addPersonel from "./personelAdd";
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
      addPerson: false,
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
    deletePersonel(item) {
      this.personelList.splice(item, 1);
    },
    AddPersonel(obje) {
      const person = {
        Id: obje.Id,
        Name: obje.Name,
        Surname: obje.Surname,
        Position: obje.Position,
        Department: obje.Department,
        Gender: obje.Gender,
      };
      this.personelList.push(person);
    },
  },
  components: {
    Popup,
    addPersonel,
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
.row {
  position: relative;
  padding: 0;
  margin: 50px 0;
  width: 100%;
}
.add-box {
  position: relative;
  width: 100%;
  margin: 20px 0;
  padding: 40px 0;
  text-align: left;
}
.form-box {
  position: relative;
  width: 32%;
  padding: 0;
  margin-bottom: 20px;
}
.form-box label {
  display: block;
  line-height: 30px;
  font-weight: bold;
}
.form-box input {
  position: relative;
  padding: 10px 20px;
  margin: 0;
  border: 1px solid #e2e2e2;
  border-radius: 7px;
  color: #000000;
}
table {
  position: relative;
  width: 100%;
  border-collapse: collapse;
}
table thead tr th,
table tbody tr td {
  padding: 10px;
  border-bottom: 1px solid #d3d3d3;
  color: #000000;
  cursor: pointer;
  text-align: left;
}
table tbody tr:nth-child(even) {
  background-color: rgb(235, 235, 235);
}
table tbody tr:hover {
  background-color: rgb(206, 206, 206);
  transition: all 0.4s ease;
}
</style>
