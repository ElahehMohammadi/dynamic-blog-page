<template>
  <div id="commentsSection" class="comments-section row col-12">
    <div class="comments-section__container container">
      <div class="comments-section__heading">
        <heading-with-lines title="دیدگاه شما"></heading-with-lines>
      </div>
      <div class="comments-section__body col-lg-9 col-md-11 col-12 mx-auto">
        <div class="comments-section__body__text col-12">
          <div class="comments-section__body__text--title">
            <img
              src="@/assets/img/icons/Bullet Rectangle.svg"
              alt="Rectangle icon-xsm"
            />
            <span>دیدگاه یا پرسش جدید</span>
          </div>
          <div class="comments-section__body__text--input">
            <textarea
              id="comment-input"
              v-model="userComment"
              rows="5"
              class="form-control"
              aria-label="With textarea"
              placeholder="دیدگاه یا پرسش خود را درباره این محتوا بنویسید..."
              @focus="writeAnotherComment"
            ></textarea>
            <span
              class="sub1 lh-base text-success validate"
              :class="isSubmitted && inputIsValid ? 'd-block' : 'd-none'"
              >دیدگاه یا پرسش شما با موفقیت ثبت شد.</span
            >
            <span
              class="sub1 lh-base text-danger validate"
              :class="isSubmitted && !inputIsValid ? 'd-block' : 'd-none'"
              >لطفا دیدگاه یا پرسش خود را به درستی وارد کنید.</span
            >
          </div>
        </div>
        <button
          class="btn comments-section__body__button border-0"
          :class="isBtnActive ? 'bg-secondary-2' : 'bg-gray-medium'"
          @click.prevent="submitData"
        >
          <span
            class="title4 lh-base"
            :class="isBtnActive ? 'text-white' : 'text-gray-light-medium'"
            >ارسال دیدگاه</span
          >
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import HeadingWithLines from '@/components/UI/HeadingWithLines.vue';
import { ref, watch } from 'vue';

//////////// SECTION //validation of textarea
const inputIsValid = ref(false);
const isBtnActive = ref(false);
const isSubmitted = ref(false);
const userComment = ref('');

watch(userComment, (newValue) => {
  if (newValue.trim() === '') {
    isBtnActive.value = false;
    return;
  }

  userComment.value = newValue;
  inputIsValid.value = true;
  isBtnActive.value = true;
  isSubmitted.value = false;
});

const submitData = function () {
  if (userComment.value.trim() === '') {
    inputIsValid.value = false;
  }
  isSubmitted.value = true;
  userComment.value = '';
};

const writeAnotherComment = function () {
  if (isSubmitted.value) {
    isSubmitted.value = false;
  }
};
</script>
