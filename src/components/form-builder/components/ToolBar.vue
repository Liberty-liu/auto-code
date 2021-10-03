<script lang="tsx">
import { reactive, toRefs, defineComponent, getCurrentInstance, h, resolveComponent } from 'vue'
import componentsConfig from './componentsConfig'
import { ComponentInternalInstance } from '@vue/runtime-core'
import draggable from 'vuedraggable'
// import _ from 'lodash'

export default defineComponent({
  name: 'ToolBar',
  components: {
    draggable
  },
  setup() {
    const dataMap: {
      tools: Array<object>
      list1: Array<object>
    } = reactive({
      tools: [],
      list1: [
        { name: 'Mission', id: 1 },
        { name: 'Mission', id: 2 },
        { name: 'Mission', id: 3 },
        { name: 'Mission', id: 4 }
      ]
    })
    return { ...toRefs(dataMap) }
  },
  render() {
    const {
      appContext
    } = (getCurrentInstance() as ComponentInternalInstance)
    const {
      tools,
      list1
    } = this
    const elementUi = Object.entries(appContext.components).filter(([key, params]) => {
      return /^El\S+/.test(key) ? {
        params
      } : false
    }).map(([, rest]) => rest)
    componentsConfig.forEach(({ ElementPlus: { name: name0 } }) => {
      const obj = elementUi.find(({ name: name1 }) => { return name0 === name1 })
      if (obj) {
        tools.push((obj))
      }
    })
    return (<div>
      {
        <draggable
          class="dragArea list-group"
          list={list1}
          group={{ name: 'people', pull: 'clone', put: false }}
          item-key="id">
          {tools.map((e: any) => {
            return h(resolveComponent(e.name))
          })}
        </draggable>
      }
    </div>)
  }
})
</script>

<style scoped>

</style>
