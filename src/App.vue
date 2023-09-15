<script setup>
  import{ ref } from "vue";

  const travel = ref("");
  const money = ref(0);

  const Details = ref({
    name: "",
    tel: "",
    date: "",
    time: "",
    tables: ""
  });
  
  //const travelList = ref(['Gunma','Shibuya','Akihabara','Kyoto','Fukuoka']);
  const travelList = ref([
    {name:' Yello ', price:80, size: {s:80, m: 150, l: 200}, img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6680-1024x1024.jpeg" },
    {name:'Krisp Cafe’', price: 50 , size: {s:50, m: 100, l: 150}, img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6690-1024x1024.jpeg" },
    {name:'Goon-Bread&Brunch', price: 90 , size: {s:90, m: 120, l: 150}, img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6869-1024x1024.jpeg" },
    {name:'Graincafe.cnx ', price: 100 , size: {s:100, m: 150, l: 200}, img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6701-1024x1024.jpeg" },
    {name:'Transit Number 8 ', price: 30 , size: {s:30, m: 50, l: 100}, img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6707-1024x1024.jpeg" }, 
    {name:'glin.cafe', img:"https://www.neepaiteaw.com/wp-content/uploads/2023/07/IMG_6713-1024x1024.jpeg"}
  ]);
  
  const bookingList = ref([
  ]);

  

  function booking(restaurant, details) {

  const bookingData = {
    restaurantName: restaurant.name,
    name: details.name,
    tel: details.tel,
    date: details.date,
    time: details.time,
    tables: details.tables,
  };
  
  bookingList.value.push(bookingData);

  Details.value.name = '';
  Details.value.tel = '';
  Details.value.date = '';
  Details.value.time = '';
  Details.value.tables = '';
  alert("Booking Complete!!! , Please Check Your Booking Details at The bottom of page")
}

  
  

</script>

<template>
  <h1 style="color:#AA1945 ;">🐱กรุณาเลือกร้านกาแฟที่คุณชอบ💞</h1> <br>
  <div class="container-input" style="background-color: #F79489;">
    <div class="cont" >
          <div class="text-input">
            Name &nbsp; <input type="text" v-model="Details.name" required> 
          </div>
          <div class="text-input">
            Tel &nbsp; <input type="tel" v-model="Details.tel" required> 
          </div>
          <div class="text-input">  
            DD/MM/YYYY &nbsp; <input type="date" v-model="Details.date" required>
          </div>
          <div class="text-input">
            Time &nbsp; <input type="time" v-model="Details.time" required>
          </div>
          <div class="text-input">
            Tables &nbsp; <input type="number" v-model="Details.tables" required> 
          </div>
    </div>
  </div>
  <div class="container text-center" style="background-color: ; border-radius: 20px;">
    <div class="row" align="center">
      <div class="col" v-for="(item, index) in travelList" :key="index">
        <div class="card" style="width: 18rem; background-color: #F8AFA6; margin: 25px; border-radius: 30px;">
          <img :src="item.img" class="card-img-top" alt="...">
          <div class="card-body">
            <h5 class="card-title">{{ item.name }}</h5>
             <br>
            <a href="#" class="btn" @click="booking(item, Details)">จองโต๊ะ</a>
          </div>
        </div>
      </div>
    </div>
  </div> <br>
  <table class="table table-dark table-striped" v-if="bookingList.length > 0">
  <thead>
    <h4>Details</h4>
    <tr>
      <th scope="col">ชื่อร้าน</th>
      <th scope="col">ชื่อผู้จอง</th>
      <th scope="col">เบอร์โทร</th>
      <th scope="col">วัน/เดือน/ปี</th>
      <th scope="col">เวลา</th>
      <th scope="col">จำนวนโต๊ะ</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(booking, index) in bookingList" :key="index">
      <td>{{ booking.restaurantName }}</td>
      <td>{{ booking.name }}</td>
      <td>{{ booking.tel }}</td>
      <td>{{ booking.date }}</td>
      <td>{{ booking.time }}</td>
      <td>{{ booking.tables }}</td>
    </tr>
  </tbody>
</table> <br>


</template>

