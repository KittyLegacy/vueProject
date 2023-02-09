<template>
    <div class=" m-4 flex justify-between flex-wrap">

        <div v-for="(item, index) in data" class="card w-100 glass m-4 p-4">
            <figure><img :src="item.image" style="width:300px; height:200px" alt="apartment" /></figure>
            <div class="card-body">
                <h2 class="card-title">{{ item.address }}</h2>
                <p>{{ item.floor }}</p>
                <p>{{ item.door }}</p>
                <div class="card-actions justify-end">
                    <Button @callBack="handleClick(item.aid)" type="primary" label="Check Inventory"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import apartments from '../apartments'
import {onMounted} from 'vue'
import Button from '../components/Button.vue'

   export default {
  components: {
    Button
  },
  setup() {
      const data = ref([])
        onMounted(() => {
    console.log("check")

    // data.value = JSON.parse(localStorage.getItem('items'))
    // if (!data) {
       data.value = [
            {
                aid: 1,
                image: "https://images.pexels.com/photos/1643384/pexels-photo-1643384.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
                address: "Bishan Park, Block 15",
                floor: "3rd Floor",
                door: "Unit: #03-88",
                inventory: [
            {
               "name": "fridge",
               "quantity": "3"
            },
            {
                "name": "ac",
                "quantity": "4"
            },
            {
                "name":"tv",
                "quantity":5
            }
        ]
            },
            {
                aid: 2,
                image: "https://images.pexels.com/photos/276724/pexels-photo-276724.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
                address: "Bishan Park, Block 12",
                floor: "5th Floor",
                door: "Unit: #05-88",
                inventory: []
            },
            {
                aid: 3,
                image: "https://images.pexels.com/photos/276724/pexels-photo-276724.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
                address: "Bishan Park, Block 3",
                floor: "1st Floor",
                door: "Unit: #01-80",
                inventory: []
            },
            {
                aid: 4,
                image: "https://images.pexels.com/photos/1571468/pexels-photo-1571468.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
                address: "Bishan Park, Block 3",
                floor: "1st Floor",
                door: "Unit: #01-88",
                inventory: []
            }
        ]
    })
    const handleClick = (id) => {
        navigateTo('/apartments/' + id)
    }
    return {
        data,
        handleClick
    }
  }
}
</script>