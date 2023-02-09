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

    data.value = JSON.parse(localStorage.getItem('items'))
    if (!data) {
      localStorage.setItem("items", JSON.stringify(apartments))
      }
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