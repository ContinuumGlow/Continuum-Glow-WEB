<template>
  <div>
    <div class="bg-white">
      <!-- Hero Section -->
      <div class="hero flex items-end justify-start h-[27.5rem] md:h-[37.5rem]">
        <li class="list-none pl-4">
            <h1 class="hero-title text-left md:pl-[1.15rem] text-[18.488vw] md:text-[9vw] font-medium">{{$t('services.title')}}</h1>
        </li>
      </div>
    </div>


    <div class="bg-white">
        <!-- Services Grid -->
      <ServicesGrid />
    </div>

  <!-- Black Section with Logo, Title, and Text -->
  <div class="black-section flex items-center justify-center py-28">
      <div class="flex items-center justify-center space-x-4 md:space-x-8 mx-24 md:mx-32">
         <div class="flex flex-col items-center gap-y-4">
         <img src="/bb.png" alt="Your Logo" class="logo w-28 h-28">
          <h1 class=" text-white mb-4 text-[32px]">{{$t('services.blacktitle')}}</h1>
          <p class=" text-white text-[18px] text-center w-[60%] mb-12">
            {{$t('services.blacktext')}}
          </p>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
    head() {
      return {
        title: 'Services - Your Website Name',
        meta: [
          {
            hid: 'description',
            name: 'description',
            content: 'Read our policies regarding privacy, cookies, and more.',
          },
        ],
      };
    },
    methods: {
    localePath(routeName) {
  const locale = this.$i18n.locale;
  return locale === 'en' ? `/${routeName}` : `/${locale}/${routeName}`;
      },
    }
  };
  </script>

<style scoped>
.hero {
  background-color: #02BDFF;
  text-align: center;
}

.hero-title {
  color: #ffffff;
}

.black-section {
  background-color: #000;
  color: #fff;
}

@media (max-width: 768px) {
  .black-section {
    flex-direction: column;
    text-align: center;
  }

  .black-section img {
    margin-bottom: 20px;
  }
}
</style>
