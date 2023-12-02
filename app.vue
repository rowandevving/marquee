<script setup>

  let id = 0
  const cards = ref([
    { id: id++ },
    { id: id++ },
    { id: id++ }
  ])

  const qqTypes = [{
    label:'Multiple choice',
    icon:'i-heroicons-list-bullet'
  },{
    label:'Text answer',
    icon:'i-heroicons-pencil-square'
  }, {
    label:'Gap fill',
    icon:'i-heroicons-puzzle-piece'
  }]
</script>

<template>
  <div>
    <UCard :ui="{rounded:false}" >
      <template #header>
        <h1 style="font-size: 2rem" align="center"><strong>Marquee pack creation tech demo</strong></h1>
      </template>
      <ul>
        <li v-for="card in cards" :key="card.id">
          <UCard>
            <p><strong>Question type</strong></p>
            <br>
            <UTabs :items="qqTypes">
              <template #default="{ item, index, selected }">
                <div class="flex items-center gap-2 relative truncate">
                  <UIcon :name="item.icon" class="w-4 h-4 flex-shrink-0" />

                  <span class="truncate">  {{ item.label }}</span>

                  <span v-if="selected" class="absolute -right-4 w-2 h-2 rounded-full bg-primary-500 dark:bg-primary-400" />
                </div>
              </template>
            </UTabs>
            <br>
            <p><strong>Question</strong></p>
            <br>
            <UTextarea></UTextarea>
            <br>
            <p><strong>Answer</strong></p>
            <br>
            <UTextarea></UTextarea>
          </UCard>
          <br>
        </li>
      </ul>
    </UCard>
  </div>
</template>
