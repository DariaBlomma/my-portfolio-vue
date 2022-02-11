<template>
        <div
          v-if="index === activeSlide"
          :class="['slide', {'active': index === activeSlide}]"
        >
          <button
            :class="['btn-img', slide['btn-img-class']]"
            @mouseenter="openSlideInfo"
            @mouseleave="hideSlideInfo"
          />
          <button
            v-if="showSlideInfo"
            :class="['btn-info', slide['btn-info-class']]"
          >
            <h2 class="secondary-title">{{slide.title}}</h2><br>
            <div v-if="slide.description" class="description">
              <b>Краткое описание: </b>
              <span
                v-if="slide.description.text"
                class='short-description'
              >
                {{slide.description.text}}
              </span>
              <ul v-if="slide.description.list">
                <li v-for="item in slide.description.list" :key="item">
                  {{item}}
                </li>
              </ul>
            </div>
            <b>Есть:</b>
            <ul :class="{'big-list': slide.hasBigList}">
              <li v-for="(skill, index) in slide.skills" :key="skill + index">
                {{skill}}
              </li>
            </ul>
          </button>
        </div>
</template>
<script>
export default {
  name: 'Slide',
  props: {
    slide: {
      type: Object,
      required: true,
    },
    index: {
      type: Number,
      required: true,
    },
    activeSlide: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      showSlideInfo: false,
    };
  },
  methods: {
    openSlideInfo() {
      this.showSlideInfo = true;
    },
    hideSlideInfo() {
      this.showSlideInfo = false;
    },
  },
};
</script>
