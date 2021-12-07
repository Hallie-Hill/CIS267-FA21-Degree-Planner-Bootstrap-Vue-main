<template>
    <div class="semesters">
        <div class="col-lg-6 semester-schedules">
            <h3>Semester Schedules</h3>

            <div
              v-for="schedule in schedules"
              v-bind:key="schedule.id"
              class="accordion my-4"
              id="schedule.id"
            >
              <div class="accordion-item">
                <h2
                  class="accordion-header"
                  id="fall2019heading"
                  v-b-toggle:[schedule.collapseId]
                >
                  <div class="">
                    <h4 class="my-0">{{ schedule.name }}</h4>
                  </div>
                </h2>
                <b-collapse :id="schedule.collapseId">
                  <div class="accordion-body">
                    <table class="table table-hover">
                      <thead>
                        <th>Course</th>
                        <td></td>
                        <td></td>
                        <th>Credits</th>
                      </thead>
                      <tr 
                      v-for="classes in schedule.classes"
                      v-bind:key="classes.id">
                        <td>BIB 121</td>
                        <td>
                          <span class="fw-bold"> The Life of Christ </span>
                        </td>
                        <td>
                          <span class="badge bg-primary"> LAC </span>
                        </td>
                        <td>2</td>
                      </tr>
                      <!-- <tr>
                        <td></td>
                        <td></td>
                        <td></td>
                        <td class="fw-bold">14</td>
                      </tr> -->
                    </table>
                  </div>
                </b-collapse>
              </div>
            </div>
          </div>
        
    </div>
</template>

<script>
export default {
  props: {
  schedules: Array
},
data() {
    return{
      courses: [
        { id: "CIS171", name: "Computer Programming I" },
        { id: "CIS211", name: "Intro to Web Design" },
      ],
    }
}
};



</script>

<style scoped>

</style>