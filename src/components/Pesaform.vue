<template>
  <div>
    <div class="jumbotron">
      <h5 class="card-title">Pesaform</h5>
      <h6 class="card-subtitle">ID: {{pesaform._id}}</h6>
      <div class="level-list">
        <div class="list-title">
          <h3>Level</h3>
          <h3>Name</h3>
        </div>
        <ul class="list-group">
          <li v-for="index in 8" :key="index" class="list-group-item">
            <h4>{{index - 1}}</h4>
            <h6 v-if="pesaform.users.length >= index">{{pesaform.users[0].name}}</h6>
            <h6 v-else>Not filled</h6>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pesaform: {}
    };
  },
  mounted() {
    fetch(`https://egoparkeastafrica.com/api/pesaform/id/${this.ID}`)
      .then(res => res.json())
      .then(res => (this.pesaform = res))
      .catch(err => console.log(err));
  },
  props: ["ID"]
};
</script>

<style scoped>
.list-group-item,
.list-title {
  display: flex;
  justify-content: space-between;
}
.level-list {
  margin-top: 20px;
}
.jumbotron {
  box-shadow: -1px 2px 5px #343a40, 1px 2px 5px #343a40;
}
</style>
