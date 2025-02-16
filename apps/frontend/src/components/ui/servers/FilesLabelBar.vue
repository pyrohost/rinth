<template>
  <div
    aria-hidden="true"
    class="sticky top-12 z-20 hidden h-8 w-full select-none flex-row items-center border-0 border-b border-solid border-bg-raised bg-bg text-xs sm:flex"
  >
    <button
      :class="[
        'mr-2 flex h-full w-full appearance-none items-center gap-1 bg-transparent px-0 text-left text-secondary',
        { 'font-semibold !text-contrast': sortField === 'name' },
      ]"
      @click="$emit('sort', 'name')"
    >
      <div class="min-w-[56px]"></div>
      <span>Name</span>
      <ChevronUpIcon v-if="sortField === 'name' && !sortDesc" class="h-3 w-3" aria-hidden="true" />
      <ChevronDownIcon v-if="sortField === 'name' && sortDesc" class="h-3 w-3" aria-hidden="true" />
    </button>
    <button
      :class="[
        'mr-2 hidden h-full min-w-[200px] appearance-none items-center justify-start gap-1 bg-transparent px-0 text-secondary md:flex',
        { 'font-semibold !text-contrast': sortField === 'created' },
      ]"
      @click="$emit('sort', 'created')"
    >
      <span>Created</span>
      <ChevronUpIcon
        v-if="sortField === 'created' && !sortDesc"
        class="h-3 w-3"
        aria-hidden="true"
      />
      <ChevronDownIcon
        v-if="sortField === 'created' && sortDesc"
        class="h-3 w-3"
        aria-hidden="true"
      />
    </button>
    <button
      :class="[
        'flex h-full min-w-[223px] appearance-none items-center justify-start gap-1 bg-transparent px-0 text-secondary md:min-w-[256px]',
        { 'font-semibold !text-contrast': sortField === 'modified' },
      ]"
      @click="$emit('sort', 'modified')"
    >
      <span>Modified</span>
      <ChevronUpIcon
        v-if="sortField === 'modified' && !sortDesc"
        class="h-3 w-3"
        aria-hidden="true"
      />
      <ChevronDownIcon
        v-if="sortField === 'modified' && sortDesc"
        class="h-3 w-3"
        aria-hidden="true"
      />
    </button>
  </div>
</template>

<script setup lang="ts">
import ChevronDownIcon from "./icons/ChevronDownIcon.vue";
import ChevronUpIcon from "./icons/ChevronUpIcon.vue";

defineProps<{
  sortField: string;
  sortDesc: boolean;
}>();

defineEmits<{
  (e: "sort", field: string): void;
}>();
</script>
