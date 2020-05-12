<template>
  <div id="calc" class="container">
    <section>
      <h1>TDEE</h1>
      <p>Simply input your height in centimeters, your weight in kilograms and your age in whole years.</p>
    </section>

    <section>
      <div class="calc card">
        <h2>Input</h2>
        <!-- <div class="gender">
          <h3>Gender</h3>
          <div class="genderwrap male">
            <p>Male</p>
            <input name="gender" type="checkbox" value="male" />
          </div>
          <div class="genderwrap female">
            <p>Female</p>
            <input name="gender" type="checkbox" value="female" />
          </div>
        </div>-->
        <div class="wrap">
          <div class="height">
            <p>Height in cm {{ height }}</p>
            <input v-model="height" />
          </div>
          <div class="weight">
            <p>Weight in kg {{ weight }}</p>
            <input v-model="weight" />
          </div>
          <div class="age">
            <p>Age in Years {{ age }}</p>
            <input v-model="age" />
            <!-- <input v-model="age" type="range" min="1" max="120"/> -->
          </div>
        </div>
      </div>
    </section>

    <section>
      <transition name="fade">
        <div v-if="age > 1 && height > 1 && weight > 1 " class="results">
          <h2>Results</h2>
          <div class="card">
            <div class="bmr">
              <h3>BMR</h3>
              <p>{{ bmr.toFixed() }}</p>
            </div>
          </div>
          <div class="card">
            <div class="bmr">
              <h3>TDEE</h3>
              <ul>
                <li>
                  <p>Sedentary:</p>
                  <p>{{ (bmr * 1.2).toFixed(0) }} Kcal</p>
                </li>
                <li>
                  <p>Lightly Active:</p>
                  <p>{{ (bmr * 1.375).toFixed(0) }} Kcal</p>
                </li>
                <li>
                  <p>Moderately Active:</p>
                  <p>{{ (bmr * 1.55).toFixed(0) }} Kcal</p>
                </li>
                <li>
                  <p>Very Active:</p>
                  <p>{{ (bmr * 1.725).toFixed(0) }} Kcal</p>
                </li>
                <li>
                  <p>Extremely Active:</p>
                  <p>{{ (bmr * 1.9).toFixed(0) }} Kcal</p>
                </li>
              </ul>
            </div>
          </div>
          <div class="card">
            <div class="details">
              <p>
                Sedentary
                <span>(little or no exercise)</span>
              </p>
              <p>
                Light activity
                <span>(light exercise/sports 1 to 3 days per week)</span>
              </p>
              <p>
                Moderate activity
                <span>(moderate exercise/sports 3 to 5 days per week)</span>
              </p>
              <p>
                Very active
                <span>(hard exercise/sports 6 to 7 days per week)</span>
              </p>
              <p>
                Extremly active
                <span>(very hard exercise/sports 6 to 7 days per week and physical job)</span>
              </p>
            </div>
          </div>
        </div>
      </transition>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      height: '',
      weight: '',
      age: '',
      male: '',
      female: ''
    }
  },
  computed: {
    bmr: function() {
      return (
        this.height * (6.25).toFixed(2) +
        this.weight * (9.99).toFixed(2) -
        this.age * (4.92).toFixed(2)
      )
    },
    tdee: function() {
      return this.bmr * 1.1
    }
  }
}
</script>

<style lang="scss" scoped>
@import 'assets/css/setup/variables';
section {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  margin-top: 5rem;
  h2 {
    margin-bottom: 5rem;
  }
  .card {
    margin: 1rem;
    padding: 3rem;
    box-shadow: $boxshadow1;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    &.gender {
      display: flex;
      .genderwrap {
        align-items: baseline;
        display: flex;
        justify-content: space-between;
        width: 100%;
      }
    }
    .details {
      p {
        text-align: left;
        margin-bottom: 1.5rem;
        span {
          display: block;
          font-weight: 300;
          font-size: 80%;
          margin-top: 0.5rem;
        }
      }
    }
  }
}

.results {
  .bmr {
    text-align: left;
    width: 100%;
  }
  ul {
    padding: 0;

    li {
      display: flex;
      justify-content: space-between;
    }
  }
}
</style>
