<template >
    <div :class="[backgroundColorClass]" class="px-12 py-20 md:px-24 md:py-28 space-y-6 ">
    <h1 :class="{'custom-main-page-title': isMainPage}">{{ $t('footerForm.title') }}</h1>
    <form 
    @submit.prevent="handleSubmit"
    name="contact"
    class="space-y-4" 
    method="POST" 
    netlify
    data-netlify-honeypot="bot-field"
    >
      <input class="hidden" name="bot-field">
      <div class="flex flex-col">
        <input type="text" id="inputname" name="name" :class="{'custom-main-placeholder': isMainPage}" :placeholder="$t('footerForm.namePlaceholder')" minlength="5" required class="text-input p-6 rounded-md">
      </div>
      <div class="flex flex-col">
        <input type="text" id="inputcompany" name="company" :class="{'custom-main-placeholder': isMainPage}" :placeholder="$t('footerForm.companyPlaceholder')" required class="text-input p-6 rounded-md">
      </div>
      <div class="flex flex-col">
        <input type="email" id="inputemail" name="email" :class="{'custom-main-placeholder': isMainPage}" :placeholder="$t('footerForm.emailPlaceholder')" minlength="5" required class="text-input p-6 rounded-md">
      </div>
      <button type="submit" :class="{'custom-main-page-style': isMainPage}" class="bg-black text-white p-6 w-full rounded-md hover:bg-gray-800 shadow-md shadow-transparent">
    {{ $t('footerForm.buttonText') }}
  </button>      <div>
        <label class="inline-flex items-center">
          <input type="checkbox" class="form-checkbox h-5 w-5 text-blue-600" required>

          <li :class="{'custom-main-policy': isMainPage}" class="list-none text-white pl-1 underline">
            <NuxtLink to="/polices">
              {{ $t('footerForm.privacyPolicy') }}
            </NuxtLink>
          </li>
          
        </label>
      </div>
    </form>
    <span v-if="isSubmitted" class="confirmation-message">{{ $t('footerForm.confirmationMessage') }}</span>
  </div>
</template>


<script>
export default {
  data() {
    return {
      isSubmitted: false
    };
  },
  computed: {
    isMainPage() {
      return this.$route.name.startsWith('index'); // Assuming 'index' is the route name for your main page
    },
  backgroundColorClass() {
    let bgColorClass;

    if (this.$route.name.startsWith('about')) {
      bgColorClass = 'bg-color-2';
    } else if (this.$route.name.startsWith('services')) {
      bgColorClass = 'bg-color-3';
    } else if (this.$route.name.startsWith('polices')) {
      bgColorClass = 'bg-color-4';
    } else {
      bgColorClass = 'bg-color-1'; // Default color
    }

    console.log("Current route:", this.$route.name, "Background class:", bgColorClass);

    return bgColorClass;
  }
},

  methods: {
    handleSubmit() {
      this.isSubmitted = true;
    }
  }
};
</script>


<style scoped>
.bg-color-1 { background-color: #ffffff;}
.bg-color-2 { background-color: #da3b3b; }
.bg-color-3 { background-color: #02BDFF; }
.bg-color-4 { background-color: #fe5420; }

.custom-main-page-style {
  background-color: #000000;
  color: #ffffff;
  transition: background-color 0.3s ease, color 0.3s ease;
}

  .custom-main-page-style:hover {
    background-color: #ffffff;
    color: #000000;
  }


.custom-main-page-title{
color: #000000;

}
.custom-main-policy{
  color: #65686a;
}
.custom-main-placeholder{
border-color: #000000;
border-width: 0.6px;
}


h1{
  font-family: 'Georgia', sans-serif;
  color: #ffffff;
  line-height: 90%; 
  font-size: 2rem;
  letter-spacing: 0.125rem;
  opacity: 0.9;
}
.text-input {
  font-size: 1.25rem;
  font-family: 'Helvetica Neue Medium', sans-serif;
}

::placeholder {
  color: #000000;
  opacity: 0.30; 
  font-size: 1.25rem;
}

input:focus::placeholder {
  opacity: 0.90;
}

button {
  font-size: 1.2rem;
  font-family: 'Helvetica Neue Medium', sans-serif;
  font-weight: 500;
  transition: background-color 0.3s ease, color 0.3s ease;
}
button:hover {
  background-color: #ffffff;
  color: #000000;
}
.confirmation-message {
  animation-duration: 2s;
  color: rgb(0, 255, 0);
  margin-top: 1rem;
}

</style>
