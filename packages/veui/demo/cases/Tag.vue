<template>
<article>
  <h1><code>&lt;veui-tag&gt;</code></h1>
  <section>
    <veui-checkbox v-model="bordered">带边框样式</veui-checkbox>
  </section>
  <section>
    <h2>不同尺寸</h2>
    <div>
      <veui-tag
        v-for="size in sizes"
        :key="size"
        :ui="size + (bordered ? ' bordered' : '')"
      >
        {{ size }}
      </veui-tag>
    </div>
  </section>

  <section>
    <h2>不同样式</h2>
    <div>
      <veui-tag
        v-for="type in types"
        :key="type"
        :type="type"
        :ui="bordered ? 'bordered' : ''"
      >
        {{ type }}
      </veui-tag>
    </div>
  </section>

  <section>
    <h2>可移除标签</h2>
    <div>
      <veui-tag
        v-for="(team, index) in teams2"
        :key="team"
        :type="types[index]"
        :ui="bordered ? 'bordered' : ''"
        closable
        @close="handleClose(team)"
      >
        {{ team }}
      </veui-tag>
    </div>
  </section>

  <section>
    <h2>可移除标签（小）</h2>
    <div>
      <veui-tag
        v-for="(team, index) in teams"
        :key="team"
        :type="types[index]"
        closable
        :ui="'s' + (bordered ? ' bordered' : '')"
        @close="handleClose(team)"
      >
        {{ team }}
      </veui-tag>
    </div>
  </section>

  <section>
    <h2>选择性标签</h2>
    <div>
      <veui-tag
        v-for="type in types"
        :key="type"
        :type="type"
        :selected.sync="selected"
        :ui="bordered ? 'bordered' : ''"
        selectable
      >
        {{ type }}
      </veui-tag>
    </div>
  </section>

  <section>
    <h2>禁用标签</h2>
    <div>
      <veui-tag
        v-for="type in types"
        :key="type"
        :type="type"
        :selected.sync="selected"
        :ui="bordered ? 'bordered' : ''"
        disabled
        selectable
      >
        {{ type }}
      </veui-tag>
    </div>
    <div style="margin-top: 20px">
      <veui-tag
        v-for="type in types"
        :key="type"
        :type="type"
        :ui="bordered ? 'bordered' : ''"
        disabled
        closable
      >
        {{ type }}
      </veui-tag>
    </div>
  </section>
</article>
</template>

<script>
import { Tag, Checkbox } from 'veui'
import toastManagers from 'veui/managers/toast'

export default {
  name: 'tag-demo',
  components: {
    'veui-tag': Tag,
    'veui-checkbox': Checkbox
  },
  data () {
    return {
      teams: ['湖人', '火箭', '猛龙', '马刺', '勇士'],
      teams2: ['湖人', '火箭', '猛龙', '马刺', '勇士'],
      types: ['default', 'info', 'success', 'warning', 'error'],
      sizes: ['s', 'm', 'default'],
      selected: false,
      bordered: false
    }
  },
  methods: {
    handleClose (name) {
      toastManagers.success(name + '赢了')
    }
  }
}
</script>

<style scoped>
.veui-tag {
  margin-right: 15px;
}
</style>
