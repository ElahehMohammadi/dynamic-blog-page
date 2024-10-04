<template>
  <footer class="col-12 row bg-gray-light">
    <div class="row container">
      <div
        class="row container-fluid justify-content-sm-start align-items-start"
      >
        <div class="col-lg col-lg-7 col-md-12 description">
          <a href="#">
            <img
              class="logo"
              alt="SokanAcademi logo"
              src="@/assets/img/icons/Logo.svg"
            />
          </a>
          <p class="sub1">
            ما در سکان‌آکادمی معتقدیم همه‌ی انسان‌ها حق دارند، به آموزش باکیفیت
            و کم‌هزینه دسترسی آسان داشته باشند و همه‌ی افراد می‌توانند با آموزش
            درست، زندگی فردی و اجتماعی خود را بهتر کنند. با توجه به تخصص تیم ما
            در حوزه‌ی IT و نیاز روزافزون بازار کار به متخصصان این حوزه، تولید و
            عرضه‌ی محتوای مهارت‌محور و تخصصی را در حوزه‌ی IT جدی‌تر دنبال کردیم.
            در این راه از ابتدای انتخاب مسیر متناسب با توانایی و امکانات دانشجو
            تا یادگیری، تمرین، کسب مهارت تخصصی و عمومی، و در نهایت معرفی به
            بازار کار همراه او هستیم...
          </p>
        </div>
        <span class="col-lg d-none d-lg-block order-2"></span>
        <the-footer-links
          v-for="linkSection in linkSections"
          :key="linkSection"
          :link-name="linkSection.linkName"
          :links-title="linkSection.linkTitle"
          :links="linkSection.links"
        ></the-footer-links>
      </div>
      <span class="copy-right title4 lh-lg">
        کلیه حقوق مادی و معنوی این وب‌سایت متعلق به سکان آکادمی می‌باشد.
      </span>
    </div>
  </footer>
</template>

<script setup>
import TheFooterLinks from '@/components/theFooter/TheFooterLinks.vue';

const fastAccess = [
  'درباره ما',
  'تماس با ما',
  'همکاری با ما',
  'شرایط و قوانین',
];
const services = [
  'دوره‌های آموزشی',
  'وبلاگ',
  'سکان پلاس',
  'رادیوفول‌استک',
  'فن‌واژه',
];
const linkSections = [
  { linkTitle: 'دسترسی سریع', linkName: 'fast-access', links: fastAccess },
  { linkTitle: 'خدمات سکان آکادمی', linkName: 'services', links: services },
];
</script>
