<template>
  <q-page padding>
    <q-list separator bordered>
      <draggable
        v-model="list"
        item-key="name"
        @start="drag = true"
        @end="drag = false"
        handle=".handle"
      >
        <template #item="{ element }">
          <q-item>
            <q-item-section>
              {{ element.place }}
            </q-item-section>
            <q-item-section avatar>
              <q-icon class="handle" name="menu"></q-icon>
            </q-item-section>
          </q-item>
        </template>
      </draggable>
    </q-list>

    <q-page-sticky position="bottom-right" :offset="[18, 18]">
      <q-btn
        round
        size="lg"
        color="accent"
        icon="add"
        @click="addOrderPlace = true"
      />
    </q-page-sticky>
    <q-dialog v-model="addOrderPlace" persistent>
      <q-card style="min-width: 350px">
        <q-card-section class="column">
          <q-select
            filled
            v-model="placeId"
            use-input
            hide-selected
            fill-input
            input-debounce="0"
            :options="options"
            @filter="filterFn"
          >
            <template v-slot:no-option>
              <q-item>
                <q-item-section class="text-grey"> No results </q-item-section>
              </q-item>
            </template>
          </q-select>
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Cancel" color="primary" v-close-popup />
          <q-btn flat label="Turn on Wifi" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Draggable from 'vuedraggable';

const drag = ref(false);
const placeId = ref('');
const selectOptions = [
  'Option 1',
  'Option 2',
  'Option 3',
  'Option 4',
  'Option 5',
];

const options = ref(selectOptions);

const addOrderPlace = ref(false);
const list = ref([{ place: 'place1' }, { place: 'place2' }]);

function filterFn(val: any, update: any) {
  update(() => {
    const needle = val.toLowerCase();
    options.value = selectOptions.filter(
      (v: any) => v.toLowerCase().indexOf(needle) > -1
    );
  });
}
</script>

<style scoped lang="scss">
.handle {
  cursor: move;
}
</style>
