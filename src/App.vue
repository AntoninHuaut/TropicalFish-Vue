<script setup lang="ts">
import { computed, ref } from "vue";

const texturesType: string[] = ["Default", "64x64"]
const types: string[] = ["betty", "blockfish", "brinely", "clayfish", "dasher", "flopper", "glitter", "kob", "snooper", "spotty", "stripey", "sunstreak"]
const colors: string[] = ["blue", "brown", "cyan", "gray", "green", "light_blue", "light_gray", "lime", "magenta", "orange", "pink", "purple", "red", "white", "yellow"]

let textureType = ref(texturesType[0])
let type = ref(types[0])
let primaryColor = ref(colors[0])
let secondaryColor = ref(colors[0])

const imgSrc = computed(() => `/${textureType.value.toLowerCase()}/${type.value}/${primaryColor.value}/${secondaryColor.value}.png`)
</script>

<template>
  <div class="flex items-center justify-center min-h-screen bg-gray-100">
    <div>
      <div class="px-8 py-6 bg-white shadow-lg">
        <div class="flex space-x-8 mt-4">
          <div class="w-32">
            <label class="block" for="texture_type">Texture type</label>
            <select v-model="textureType" id="texture_type" class="w-full px-4 py-2 mt-2 border rounded-md">
              <option :value="loopType" v-for="loopType in texturesType">
                {{ loopType }}
              </option>
            </select>
          </div>
          <div class="w-32">
            <label class="block" for="fish_type">Fish type</label>
            <select v-model="type" id="fish_type" class="w-full px-4 py-2 mt-2 border rounded-md">
              <option :value="loopType" v-for="loopType in types">
                {{ loopType }}
              </option>
            </select>
          </div>
        </div>
        <div class="flex space-x-8 mt-4">
          <div class="w-32">
            <label class="block" for="primary_color">Primary color</label>
            <select v-model="primaryColor" id="primary_color" class="w-full px-4 py-2 mt-2 border rounded-md">
              <option :value="loopColor" v-for="loopColor in colors">
                {{ loopColor }}
              </option>
            </select>
          </div>

          <div class="w-32">
            <label class="block" for="secondary_color">Secondary color</label>
            <select v-model="secondaryColor" id="secondary_color" class="w-full px-4 py-2 mt-2 border rounded-md">
              <option :value="loopColor" v-for="loopColor in colors">
                {{ loopColor }}
              </option>
            </select>
          </div>
        </div>
      </div>

      <div class="px-8 py-6">
        <img class="h-96" :src="imgSrc" alt="Fish" />
      </div>
    </div>
  </div>
</template>