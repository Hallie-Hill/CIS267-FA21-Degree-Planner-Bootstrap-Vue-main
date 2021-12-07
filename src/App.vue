<template>
  <div id="app" class="d-flex flex-column min-vh-100">
    <!-- Main Content -->
    <main class="flex-fill">
      <div class="container-fluid">
        <div class="row mb-5">
          <h1>Degree Planner</h1>
        </div>
        <div class="row main-content">
          <!-- Classes -->
          <div class="col-lg-4 required-classes">
            <h3>Required Classes</h3>

            <b-tabs content-class="mt-3">
              <!-- LAC Requirements -->

              <b-tab title="LAC" active>
                <div id="lac">
                  <div class="my-4 text-left" id="lac-reqs">
                    <CourseInfoCard @add-course="addCourse" :course=c  v-for="c in lacCourses" :options="options" :key="c['Course ID']" />
                  </div>
                </div>
              </b-tab>

              <b-tab title="IDD">
                <div id="lac">
                  <div class="my-4 text-left" id="lac-reqs">
                    <CourseInfoCard @add-course="addCourse" :course=c v-for="c in iddCourses" :options="options" :key="c['Course ID']" />
                  </div>
                </div>
              </b-tab>
            </b-tabs>
          </div>

          <!-- Semester Schedules -->
          <div class="col-lg-6 semester-schedules">
            <SemesterSchedule
            :schedules="schedules"> 
            </SemesterSchedule>
          </div>

          <!-- Table of Contents Sidebar -->
          <div class="col-lg-2 position-sticky top-0 h-100 ps-5 toc">
            <nav>
              <p class="text-muted">On this page</p>
              <ul>
                <li><a href="#fall2020">Fall 2020</a></li>
                <li><a href="#spring2021">Spring 2021</a></li>
                <li><a href="">Fall 2021</a></li>
                <li><a href="">Spring 2022</a></li>
                <li><a href="">Fall 2022</a></li>
                <li><a href="">Spring 2023</a></li>
                <li><a href="">Fall 2023</a></li>
                <li><a href="">Spring 2024</a></li>
              </ul>
            </nav>
          </div>
        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer class="bg-dark text-light py-4">
      <div class="container-fluid">
        <div class="row">
          <div class="col">
            <p>Made with ❤️ by FHU students!</p>
          </div>

          <div class="col-md-3">
            <p>&copy; 2021 Freed-Hardeman University</p>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import CourseInfoCard from './components/CourseInfoCard.vue'
import SemesterSchedule from './components/SemesterSchedule.vue'
import lacCoursesFromFile from './lac.json'
import iddCoursesFromFile from './idd.json'

export default {
  name: "App",
  components: {
    CourseInfoCard,
    SemesterSchedule
    //HelloWorld
  },

  methods: {
    addCourse(course, semester) {
      console.log('course pushed')
      console.log(semester)
      this.schedules.forEach(item => {
        if(item.id == semester) {
          item.classes.push(course);
        }
      });
      // if (this.options.selected === this.semester) {
      //   console.log('pushed to', semester)
      //   this.course.push(this.schedules.classes);
      // }
      
     
    }
  },
  mounted() {

  },
  data() {
    return {
      schedules: [
        {
          name: "Fall 2020",
          id: "fall2020",
          collapseId: "fall2020schedule",
          classes: [],
        },
        {
          name: "Spring 2021",
          id: "spring2021",
          collapseId: "spring2021schedule",
          classes: [],
        },
        {
          name: "Fall 2021",
          id: "fall2021",
          collapseId: "fall2021schedule",
          classes: [],
        },
        {
          name: "Spring 2022",
          id: "spring2022",
          collapseId: "spring2022schedule",
          classes: [],
        },
        {
          name: "Fall 2022",
          id: "fall2022",
          collapseId: "fall2022schedule",
          classes: [],
        },
        {
          name: "Spring 2023",
          id: "spring2023",
          collapseId: "spring2023schedule",
          classes: [],
        },
        {
          name: "Fall 2023",
          id: "fall2023",
          collapseId: "fall2023schedule",
          classes: [],
        },
        {
          name: "Spring 2024",
          id: "spring2024",
          collapseId: "spring2024schedule",
          classes: [],
        },
        
      ],
      courses: [
        { id: "CIS171", name: "Computer Programming I" },
        { id: "CIS211", name: "Intro to Web Design" },
      ],

      lacCourses: lacCoursesFromFile,
      iddCourses: iddCoursesFromFile,
      options: [
        { value: null, text: "Please select an option" },
        { value: "fall2020", text: "Fall 2020" },
        { value: "spring2021", text: "Spring 2021" },
        { value: "fall2021", text: "Fall 2021" },
        { value: "spring2022", text: "Spring 2022"},
        { value: "fall2022", text: "Fall 2022" },
        { value: "spring2023", text: "Spring 2023" },
        { value: "fall2023", text: "Fall 2023" },
        { value: "spring2024", text: "Spring 2024"},
      ],
      selected: null,
    };
  },
};
</script>

<style>
#app {
  font-family: "Nunito Sans", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.toc nav {
  text-align: left;
}

.toc ul {
  padding: 0;
  list-style: none;
}

.toc li {
  margin: 0;
  margin-bottom: 0.5rem;
}

.toc li a {
  text-decoration: none;
}

.toc li a:hover {
  text-decoration: underline;
}

.required-classes .card {
  border-left: 8px solid #0c63e4;
}
</style>
