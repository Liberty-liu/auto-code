<template>
  <el-container style="height: 500px; border: 1px solid #eee">
    <el-aside
      width="200px"
      style="background-color: rgb(238, 241, 246)"
    >
      <ToolBar />
    </el-aside>
    <el-container>
      <el-header style="text-align: right; font-size: 12px">
        1
      </el-header>
    </el-container>
  </el-container>
  <div>
    <div class="row">
      <div class="col-3">
        <h3>Draggable 1</h3>
        <draggable
          class="dragArea list-group"
          :list="list1"
          :group="{name: 'people', pull: 'clone', put: false}"
          item-key="id"
        />
      </div>

      <div class="col-3">
        <h3>Draggable 2</h3>
        <draggable
          class="dragArea list-group"
          :list="list2"
          group="people"
          @change="log"
          item-key="id"
        >
          <template #item="{element}">
            <div class="list-group-item">
              {{ element.name }}
            </div>
          </template>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'
import draggable from 'vuedraggable'
import ToolBar from './components/ToolBar.vue'
export default defineComponent({
  name: 'FormBuilder',
  components: {
    draggable,
    ToolBar
  },
  setup() {
    // const win: any = window
    // win.vm = internalInstance
    // // console.log(ComponentOptions)
    // console.log(Object.entries(internalInstance?.appContext.components as object).filter(([key]) => /^El\s+/.test(key)))
    // console.log(internalInstance!.root.appContext.components.filter(() => true))
    const dataMap = reactive({
      group: 'mission',
      tableData: {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      },
      list1: [
        { name: 'Mission', id: 1 },
        { name: 'Mission', id: 2 },
        { name: 'Mission', id: 3 },
        { name: 'Mission', id: 4 }
      ],
      list2: [
        { name: 'Mission', id: 5 },
        { name: 'Mission', id: 6 },
        { name: 'Mission', id: 7 }
      ],
      list3: [
        { name: 'Mission', id: 8 },
        { name: 'Mission', id: 9 },
        { name: 'Mission', id: 10 }
      ]
    })
    return { ...toRefs(dataMap) }
  }
})
</script>

<style scoped>

</style>
