<template>
  <div class="section">
    <div>
      <h2>Einschulungen</h2>
      <div class="courseContainer">
        <Course
          v-for="course of courses"
          :key="course.id"
          :course="course"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Course from '@/components/Course'
export default {
  components: {
    Course
  },
  middleware: 'authenticated',
  data () {
    return {}
  },
  computed: {
    memberCourses () {
      return this.$store.state.memberCourses
    },
    courses () {
      return this.$store.state.courses
    },
    user () {
      return this.$store.state.user
    }
  },
  created () {
  },
  methods: {
  }
}
</script>

<style lang="scss">
@import '@/assets/scss/styles.scss';
.section {
  display: flex;
  flex-direction: column;
}
.courseContainer {
  display: flex;
  flex-wrap: wrap;
}
.link-with-arrow {
  .link-text {
    a {
      text-transform: uppercase;
      color: $color-blue;
    }
    margin: 1em 0 .5em;
    display: flex;
    align-items: center;
    min-width: 200px;
    .link-arrow {
      border-top: $color-blue 1px solid;
      width: 1em;
      position: relative;
      margin-right: .3em;
      &:before {
        position: absolute;
        right: 0;
        content: "";
        border-top: $color-blue 1px solid;
        border-right: $color-blue 1px solid;
        transform: rotateZ(45deg);
        transform-origin: top right;
        height: .3em;
        width: .3em;
        margin-top: -.5px;
      }
    }
  }
}

</style>
