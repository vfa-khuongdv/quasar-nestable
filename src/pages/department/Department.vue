<template>
  <div class="q-pa-lg">
    <q-breadcrumbs active-color="primary" style="font-size: 14px">
        <q-breadcrumbs-el label="Home" icon="home" />
        <q-breadcrumbs-el label="Vitalify Asia"/>
        <q-breadcrumbs-el label="Department"/>
      </q-breadcrumbs>
    <q-card bordered flat class="my-card q-mt-md">
      <q-card-section>
        <div class="flex items-center justify-between">
          <div class="text-h6">Departments</div>
          <q-btn color="blue-4" label="Add new"></q-btn>
        </div>
      </q-card-section>
       <q-separator inset />
      <q-card-section>
        <vue-nestable v-model="nestableItems">
          <vue-nestable-handle slot-scope="{ item }" :item="item">
            <div class="flex items-center justify-between">
              <div class="menu-item">
                <q-icon name="menu" class="q-mr-xs"></q-icon>
                {{ item.text }}
              </div>
              <div class="menu-actions">
                <q-btn size="10px" dense color="green-4" rounded unelevated>
                  <q-icon name="add"></q-icon>
                </q-btn>
                <q-btn size="10px" dense color="blue-4" round unelevated>
                  <q-icon name="mode_edit_outline" size="15px"></q-icon>
                </q-btn>
                <q-btn size="10px" dense color="red-4" round unelevated>
                  <q-icon name="fas fa-trash" size="10px"></q-icon>
                </q-btn>
              </div>
            </div>
          </vue-nestable-handle>
        </vue-nestable>
      </q-card-section>
    </q-card>
  </div>
</template>

<script>
export default {
  components: {},
  data () {
    return {
      nestableItems: [
        {
          id: 0,
          text: 'IT Software',
          icon: 'home',
          children: [
            {
              id: 8,
              text: 'Frontend',
              icon: 'home',
              children: [
                {
                  id: 11,
                  text: 'VueJs'
                },
                {
                  id: 12,
                  text: 'ReactJs'
                }
              ]
            },
            {
              id: 9,
              text: 'Backend',
              icon: 'home',
              children: [
                {
                  id: 14,
                  text: 'NodeJs'
                },
                {
                  id: 16,
                  text: 'Java'
                }
              ]
            },
            {
              id: 10,
              text: 'Mobile App',
              icon: 'home',
              children: [
                {
                  id: 19,
                  text: 'Flutter'
                }
              ]
            }
          ]
        },
        {
          id: 5,
          text: 'Marketing',
          icon: 'home',
          children: [
            {
              id: 6,
              text: 'Sale 1',
              icon: 'home'
            },
            {
              id: 7,
              text: 'Sale 2',
              icon: 'home'
            }
          ]
        }
      ]
    }
  },
  created () {
    this.$q.loading.show()
  },
  mounted () {
    setTimeout(() => {
      this.$q.loading.hide()
    }, 1000)
  }
}
</script>
<style lang="scss">
@import "../../css/drag.scss";
.menu-actions {
  min-width: 80px;
  display: flex;
  justify-content: space-between;
}
</style>
