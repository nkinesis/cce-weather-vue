<template>
  <main>
    <header role="banner">
      <h1>CCE Weather</h1>
      <p>This is an example weather website for Montreal and other Canadian cities.</p>
    </header>

    <section class="recordFilter" role="search">
      <label for="city">Select your city</label>
      <select id="city" v-model=selectedCity>
        <option selected value="1">Montreal</option>
        <option value="2">City2</option>
        <option value="3">City3</option>
      </select>
    </section>

    <section class="recordList" role="main">
      <p v-if="weatherRecords && weatherRecords.length">If you are reading this, your project is working correctly!</p>
      <p v-for="record in weatherRecords" :key="record.id"> ID {{record.id}}, Condition: {{record.condition}}, City ID: {{record.cityId}}, Date: {{record.date}}, Max temp.: {{record.maxTemp}}, Min temp.: {{record.minTemp}}</p>
    </section>
  </main>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return {
      selectedCity: 1,
      weatherRecords: []
    }
  },
  beforeMount() {
    var component = this;
    fetch('/api/weatherRecords')
      .then(function (response) {
        return response.json()
      })
      .then(function (data) {
        component.weatherRecords = data
      })
      .catch(function (error) {
        console.log(error)
      })
  }
}
</script>

<style lang="scss">
main {
  text-align: left;

  .recordFilter {
    display: flex;
    width: 250px;
    height: 48px;
    align-items: center;
    margin-bottom: 30px;

    label {
      font-weight: bold;
      margin-right: 10px;
    }
  }

  .recordList {
    p {
      line-height: 1.5em;
    }
  }
}
</style>