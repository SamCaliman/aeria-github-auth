<script setup lang="ts">

const CLIENT_ID = import.meta.env.VITE_GITHUB_CLIENT_ID
const GITHUB_URL = 'https://github.com/login/oauth/authorize'

// Redirect User to github OAuth page, passing the client id as an paramenter
async function githubAuth() {
  const params = {
    response_type: 'code',
    scope: 'user',
    client_id: CLIENT_ID,
    redirect_uri: 'http://localhost:8080/redirect'
  }
  if(CLIENT_ID){
    window.open(`${GITHUB_URL}`+'?'+`${new URLSearchParams(params).toString()}`, '_self')
  }
}

</script>

<template>
  <section class="
  tw-w-full
  tw-h-[100vh]
  tw-bg-neutral-800
  tw-flex
  "> 
    <div
      class="
        tw-bg-neutral-600
        tw-rounded
        tw-w-3/5
        tw-min-w-[30rem]
        tw-p-6
        tw-flex
        tw-flex-col
        tw-rounded-md
        tw-m-auto
        tw-text-center
        tw-text-white
      "
    >
    Login With Github
    <aeria-button @click="githubAuth()">Login</aeria-button>
  </div>
  </section>
  
</template>
