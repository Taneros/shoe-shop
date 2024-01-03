<template>
      <header class="flex justify-between border-b border-slate-300 px-10 py-8">
      <div class="flex items-center gap-4">
        <img src="/logo.png" alt="Logo" class="w-10 h-10"/>
        <div>
          <h2 class="text-lx font-bold uppercase">Vue Sneakers</h2>
          <p class="text-slate-500">The Best Skeakers Shop</p>
        </div>
      </div>

      <ul class="flex items-center gap-10">
        <li class="flex items-center gap-3 text-gray-500 hover:text-black cursor-pointer">
          <img src="/cart.svg" alt="Cart">
          <b>1205 руб.</b>
        </li>
        <li class="flex items-center gap-3 text-gray-500 hover:text-black cursor-pointer">
          <img src="/heart.svg" alt="Favorites">
          <span >Закладки</span>
        </li>
        <li class="flex items-center gap-3 text-gray-500 hover:text-black cursor-pointer">
          <img src="/profile.svg" alt="Favorites">
          <span >Профиль</span>
        </li>
      </ul>
    </header>
</template>