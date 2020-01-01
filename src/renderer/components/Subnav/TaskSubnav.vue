<template>
  <nav class="subnav-inner">
    <h3>{{ title }}</h3>
    <ul>
      <li
        @click="() => nav('active')"
        :class="[ current === 'active' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <a-icon type="caret-right" />
        </i>
        <span>{{ $t('task.active') }}</span>
      </li>
      <li
        @click="() => nav('waiting')"
        :class="[ current === 'waiting' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <a-icon type="pause-circle" theme="filled"/>
        </i>
        <span>{{ $t('task.waiting') }}</span>
      </li>
      <li
        @click="() => nav('stopped')"
        :class="[ current === 'stopped' ? 'active' : '' ]"
      >
        <i class="subnav-icon">
          <a-icon type="stop" theme="filled"/>
        </i>
        <span>{{ $t('task.stopped') }}</span>
      </li>
    </ul>
  </nav>
</template>

<script>
  import '@/components/Icons/task-start'
  import '@/components/Icons/task-pause'
  import '@/components/Icons/task-stop'

  export default {
    name: 'mo-task-subnav',
    props: {
      current: {
        type: String,
        default: 'active'
      }
    },
    computed: {
      title: function () {
        return this.$t('subnav.task-list')
      }
    },
    methods: {
      nav: function (status = 'active') {
        this.$router.push({
          path: `/task/${status}`
        })
      }
    }
  }
</script>

<style lang="scss">
</style>
