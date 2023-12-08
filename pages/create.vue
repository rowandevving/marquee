<script setup>

  let id = 0
  const cards = ref([
    { id: id++ },
  ])

  const qqTypes = [{
    label:'Multiple choice',
    icon:'i-heroicons-list-bullet'
  },{
    label:'Text answer',
    icon:'i-heroicons-pencil-square'
  }]
</script>

<template>
  <div>
    <UCard :ui="{rounded:false}" >
      <template #header>
        <h1 style="font-size: 2rem" align="center"><strong>Marquee pack creation tech demo</strong></h1>
      </template>
      <UContainer :style="{maxWidth:'1000px', marginBottom:'14.6rem'}">
        <UCard>
          <UButton icon="i-heroicons-squares-plus" size="xl">Add Card</UButton>
          <br>
          <br>
          <ul>
            <li v-for="card in cards" :key="card.id">
              <UCard color="gray">
                <p><strong>Question type</strong><span :style="{float:'right'}"><UPopover><UIcon color="gray" name="i-heroicons-trash"/><template #panel>
                  <div class="p-4">
                    <p style="margin-bottom: 0.7rem; margin-top:-0.5rem;">Are you sure?</p>

                    <UButton variant="solid" color="red">Delete</UButton>
                  </div>  
                </template></UPopover></span></p>
                <br>
                <UTabs v-model="card.selected" :items="qqTypes">
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
      </UContainer>
    </UCard>
  </div>
</template>