<template>
    <div class="w-full p-4 border b-gray-200 flex items-center justify-between">
      <span class="text-xl font-semibold">
        <slot />
      </span>
      <div class="w-30 space-x-2">
        <slot name="actions" />
      </div>
    </div>
</template>