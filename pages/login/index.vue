<script setup>
definePageMeta({
  layout: "forntend",
  middleware: "guest",
});
//data From From
const form = reactive({
  email: "",
  password: "",
});
const { signIn } = useAuth();
const handleLogin = async() => {
  try {
    await signIn("credentials", {username: form.email, password: form.password });
  } catch (e) {
    console.log(e);
  }finally{
    $router.push("/admin")
  }
}
</script>
<template>
  <div class="max-w-lg w-full mx-auto mt-10 shadow-md p-5">
    <div>
      <h2 class="mt-6 text-center text-3xl font-extrabold text-primary">
        Sign in to your account
      </h2>
    </div>
    <form class="mt-8 space-y-6" @submit.prevent="handleLogin" >
      <div class="rounded-md shadow-sm">
        <div>
          <label for="email" class="sr-only">Email address</label>
          <input
            id="email"
            name="email"
            type="email"
            v-model="form.email"
            autocomplete="email"
            required
            class="mt-1 block w-full rounded-md border p-2 border-gray-300 shadow-sm focus:border-primary"
            placeholder="Email address"
          />
        </div>
        <div class="my-2">
          <label for="password" class="sr-only">Password</label>
          <input
            id="password"
            name="password"
            type="password"
            v-model="form.password"
            autocomplete="current-password"
            required
            class="mt-1 block w-full rounded-md border p-2 border-gray-300 shadow-sm focus:border-primary"
            placeholder="Password"
          />
        </div>
        <div class="flex justify-between items-center my-5">
          <NuxtLink to="/signup" class="text-green-500">Signup</NuxtLink>
          <p class="underline text-red-500 cursor-pointer">Forget password</p>
        </div>
      </div>

      <div>
        <button
          type="submit"
          class="group relative w-full flex justify-center py-2 px-4 text-sm font-medium rounded-md text-white bg-primary"
        >
          Sign in
        </button>
      </div>
    </form>
  </div>
</template>



<style></style>
