<script>
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  import { themeChange } from 'theme-change';
  import {
    BarsSolid,
    SunOutline,
    MoonOutline
  } from 'flowbite-svelte-icons';

  import Menu from './Menu.svelte';

  const theme = browser && localStorage.getItem('theme');
  onMount(() => {
    themeChange(false);
  });
</script>

<header class="flex justify-between">
  <div class="navbar bg-base-100 items-baseline">

    <div class="navbar-start">
      <div class="dropdown lg:hidden">
        <div tabindex="0" role="button" class="">
          <BarsSolid />
          <svg class="h-1 w-1" />
        </div>
        <ul tabindex="0" class="dropdown-content z-[1] menu p-2 shadow bg-base-100 rounded-box w-52">
          <Menu />
        </ul>
      </div>

      <a class="btn btn-ghost text-xl">SDM</a>
    </div>

    <div class="navbar-end">
      <div class="hidden lg:inline-flex">
        <ul class="menu menu-horizontal">
          <Menu />
        </ul>
      </div>

      <label class="swap swap-rotate">
        <input
          type="checkbox"
          data-toggle-theme="pastel,dracula"
          data-act-class="ACTIVECLASS"
          checked={theme !== 'light'}
        />
        <SunOutline class="swap-on" />
        <MoonOutline class="swap-off" />
      </label>
    </div>
  </div>
</header>
