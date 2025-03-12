<script setup>
const NuxtApp = useNuxtApp();
const loaded = ref(false);
NuxtApp.hook('page:start',()=>{
  console.log('START page')
})
const Posts=ref(1234);
const Followers=ref(567);
const Following=ref(890);
onMounted(()=>{
  Posts.value=Math.round((Math.random()*(10**4)+500)/10)*10+(Math.round(Math.random())%2);
  Followers.value=Math.round((Math.random()*(10**3)+890)/10)*10+(Math.round(Math.random())%2);
  Following.value=Math.round((Math.random()*(10**3)+350)/10)*10+(Math.round(Math.random())%2);

})

NuxtApp.hook('app:mounted', async () => {
  const { data: user, status } = await useAsyncData('user', () => $fetch('https://randomuser.me/api'));//на момент создание проекта это api почемуто не работало и лагало поэтому оно не использованно

})
NuxtApp.hook('page:finish',()=>{
  loaded.value = true;
  console.log('FINISH')
})
</script>

<template>
    <div v-if='loaded'
      class="relative flex size-full min-h-screen flex-col bg-white group/design-root overflow-x-hidden"
      style='font-family: "Plus Jakarta Sans", "Noto Sans", sans-serif;'>
      <div class="layout-container flex h-full grow flex-col">
        <div class="gap-1 px-6 flex flex-1 justify-center py-5">
          <div class="layout-content-container flex flex-col w-80">
            <div class="flex p-4 @container">
              <div class="flex w-full flex-col gap-4 @[520px]:flex-row @[520px]:justify-between @[520px]:items-center">
                <div class="flex gap-4">
                  <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full min-h-32 w-32"
                    style='background-image: url("https://images.generated.photos/Y8wUk86s3gvY80uhzCAWqCjkIXl6m31iaD5DKJIA8Hg/rs:fit:256:256/czM6Ly9pY29uczgu/Z3Bob3Rvcy1wcm9k/LnBob3Rvcy92M18w/NDYyNzM0LmpwZw.jpg");'>
                  </div>
                  <div class="flex flex-col justify-center">
                    <p class="text-[#111518] text-[22px] font-bold leading-tight tracking-[-0.015em]">Max</p>
                    <p class="text-[#60778a] text-base font-normal leading-normal">Moscow</p>
                  </div>
                </div>
                <div class="flex w-full max-w-[480px] gap-3 @[480px]:w-auto">
                  <button
                    class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-xl h-10 px-4 bg-[#f0f2f5] text-[#111518] text-sm font-bold leading-normal tracking-[0.015em] flex-1 @[480px]:flex-auto">
                    <span class="truncate">Following</span>
                  </button>
                  <button
                    class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-xl h-10 px-4 bg-[#2094f3] text-white text-sm font-bold leading-normal tracking-[0.015em] flex-1 @[480px]:flex-auto">
                    <span class="truncate">Message</span>
                  </button>
                </div>
              </div>
            </div>
            <div class="flex flex-wrap gap-3 px-4 py-3">
              <div
                class="flex min-w-[111px] flex-1 basis-[fit-content] flex-col gap-2 rounded-lg border border-[#dbe1e6] p-3 items-center text-center">
                <p class="text-[#111518] tracking-light text-2xl font-bold leading-tight">{{ Posts }}</p>
                <div class="flex items-center gap-2">
                  <p class="text-[#60778a] text-sm font-normal leading-normal">Posts</p>
                </div>
              </div>
              <div
                class="flex min-w-[111px] flex-1 basis-[fit-content] flex-col gap-2 rounded-lg border border-[#dbe1e6] p-3 items-center text-center">
                <p class="text-[#111518] tracking-light text-2xl font-bold leading-tight">{{ Followers }}</p>
                <div class="flex items-center gap-2">
                  <p class="text-[#60778a] text-sm font-normal leading-normal">Followers</p>
                </div>
              </div>
              <div
                class="flex min-w-[111px] flex-1 basis-[fit-content] flex-col gap-2 rounded-lg border border-[#dbe1e6] p-3 items-center text-center">
                <p class="text-[#111518] tracking-light text-2xl font-bold leading-tight">{{ Following }}</p>
                <div class="flex items-center gap-2">
                  <p class="text-[#60778a] text-sm font-normal leading-normal">Following</p>
                </div>
              </div>
            </div>
            <p class="text-[#111518] text-base font-normal leading-normal pb-3 pt-1 px-4">IT | Algorithms | Frontend | CTF
            </p>
            <div class="flex w-full grow bg-white @container py-3">
              <div
                class="w-full gap-1 overflow-hidden bg-white @[480px]:gap-2 aspect-[3/2] grid grid-cols-[2fr_1fr_1fr]">
                <div class="w-full bg-center bg-no-repeat bg-cover aspect-auto rounded-none row-span-2"
                  style='background-image: url("https://i0.wp.com/informationage-production.s3.amazonaws.com/uploads/2022/10/AdobeStock_79161609-scaled.jpeg?ssl=1");'>
                </div>
                <div class="w-full bg-center bg-no-repeat bg-cover aspect-auto rounded-none col-span-2"
                  style='background-image: url("https://habrastorage.org/getpro/habr/upload_files/527/9f3/9a6/5279f39a6569cc2d82708414d588a006.png");'>
                </div>
                <div class="w-full bg-center bg-no-repeat bg-cover aspect-auto rounded-none col-span-2"
                  style='background-image: url("https://i.ytimg.com/vi/kWTKneQp7-M/maxresdefault.jpg");'>
                </div>
              </div>
            </div>
          </div>
          <div class="layout-content-container flex flex-col max-w-[960px] flex-1">
            <div class="flex gap-3 p-4">
              <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10"
                style='background-image: url("https://images.generated.photos/Y8wUk86s3gvY80uhzCAWqCjkIXl6m31iaD5DKJIA8Hg/rs:fit:256:256/czM6Ly9pY29uczgu/Z3Bob3Rvcy1wcm9k/LnBob3Rvcy92M18w/NDYyNzM0LmpwZw.jpg");'>
              </div>
              <div class="flex flex-1 flex-col items-stretch gap-2">
                <div class="flex flex-col gap-1">
                  <div class="flex flex-wrap items-center gap-3">
                    <p class="text-[#111518] text-base font-bold leading-tight">Max</p>
                    <p class="text-[#60778a] text-sm font-normal leading-normal">1 day ago</p>
                  </div>
                  <p class="text-[#111518] text-base font-normal leading-normal">coding, coding and coding 🧑‍💻😊🧑‍💻
                  </p>
                </div>
              </div>
            </div>
            <div class="flex gap-3 p-4">
              <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10"
                style='background-image: url("https://images.generated.photos/Y8wUk86s3gvY80uhzCAWqCjkIXl6m31iaD5DKJIA8Hg/rs:fit:256:256/czM6Ly9pY29uczgu/Z3Bob3Rvcy1wcm9k/LnBob3Rvcy92M18w/NDYyNzM0LmpwZw.jpg");'>
              </div>
              <div class="flex flex-1 flex-col items-stretch gap-2">
                <div class="flex flex-col gap-1">
                  <div class="flex flex-wrap items-center gap-3">
                    <p class="text-[#111518] text-base font-bold leading-tight">Max</p>
                    <p class="text-[#60778a] text-sm font-normal leading-normal">2 days ago</p>
                  </div>
                  <p class="text-[#111518] text-base font-normal leading-normal">Happy birthday to my best friend!
                    🎉🎂👭
                  </p>
                </div>
              </div>
            </div>
            <div class="flex gap-3 p-4">
              <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10"
                style='background-image: url("https://images.generated.photos/Y8wUk86s3gvY80uhzCAWqCjkIXl6m31iaD5DKJIA8Hg/rs:fit:256:256/czM6Ly9pY29uczgu/Z3Bob3Rvcy1wcm9k/LnBob3Rvcy92M18w/NDYyNzM0LmpwZw.jpg");'>
              </div>
              <div class="flex flex-1 flex-col items-stretch gap-2">
                <div class="flex flex-col gap-1">
                  <div class="flex flex-wrap items-center gap-3">
                    <p class="text-[#111518] text-base font-bold leading-tight">Max</p>
                    <p class="text-[#60778a] text-sm font-normal leading-normal">4 days ago</p>
                  </div>
                  <p class="text-[#111518] text-base font-normal leading-normal">Look to my code</p>
                </div>
                <div class="bg-center bg-no-repeat aspect-video bg-cover rounded-xl w-full max-w-[360px]"
                  style='background-image: url("https://raw.githubusercontent.com/jeaye/color_coded/master/pics/trimmed_cc_t_yes_1.png");'>
                </div>
              </div>
            </div>
            <div class="flex gap-3 p-4">
              <div class="bg-center bg-no-repeat aspect-square bg-cover rounded-full size-10"
                style='background-image: url("https://images.generated.photos/Y8wUk86s3gvY80uhzCAWqCjkIXl6m31iaD5DKJIA8Hg/rs:fit:256:256/czM6Ly9pY29uczgu/Z3Bob3Rvcy1wcm9k/LnBob3Rvcy92M18w/NDYyNzM0LmpwZw.jpg");'>
              </div>
              <div class="flex flex-1 flex-col items-stretch gap-2">
                <div class="flex flex-col gap-1">
                  <div class="flex flex-wrap items-center gap-3">
                    <p class="text-[#111518] text-base font-bold leading-tight">Max</p>
                    <p class="text-[#60778a] text-sm font-normal leading-normal">5 days ago</p>
                  </div>
                  <p class="text-[#111518] text-base font-normal leading-normal">Ha ha ha...</p>
                </div>
                <div class="bg-center bg-no-repeat aspect-video bg-cover h-[300px] rounded-xl w-full max-w-[360px]"
                  style='background-image: url("https://i.pinimg.com/736x/e6/61/91/e6619184334d188b37b4f481f37e5732.jpg");'>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <img src="/loading.gif" width="150px" margin="15px" v-else></img>

</template>