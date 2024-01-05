<template>
  <div class="flex justify-between items-center mb-8">
    <h2 class="text-3xl font-bold ">Все кроссовки</h2>

    <div class="flex items-center gap-4">
      <select class="py-2 px-3 border rounded-md outline-none">
        <option>По названию</option>
        <option>По цене (дорогие)</option>
        <option>По цене (дешевые)</option>
      </select>

      <div class="relative">
        <img src="/search.svg" alt="Search"
             class="absolute top-1/2 left-3 transform -translate-y-1/2">
        <input class=" border rounded-md py-2 pl-10 pr-4 outline-none focus:border-gray-400 transition" type="text"
               placeholder="Поиск...">
      </div>
    </div>
  </div>
</template>