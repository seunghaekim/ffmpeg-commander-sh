<template>
  <div class="ffmpeg-editor">
    <!-- User can load pre-defined presets and can also access their
    custom saved presets here. -->
    <PresetsComponent />

    <!-- Input and Output protocol and filenames. -->
    <FileIOComponent />

    <!-- Tabs for each command building component.
    Format, Video, Audio, Filters and Options -->
    <b-tabs class="mt-4">
      <b-tab title="Format" class="mt-2">
        <FormatComponent />
      </b-tab>

      <b-tab title="Video" class="mt-2">
        <VideoComponent />
      </b-tab>

      <b-tab title="Audio" class="mt-2">
        <AudioComponent />
      </b-tab>

      <b-tab title="Filters" class="mt-2">
        <FiltersComponent />
      </b-tab>

      <b-tab title="Options" class="mt-2">
        <OptionsComponent />
      </b-tab>
    </b-tabs>
    <hr />

    <!-- FFmpeg generated command output with tooltips. -->
    <CommandComponent />
    <p class="disclaimer">
      *Generated options may vary based on your FFmpeg version and build configuration. Tested on
      version 4.3.1.
    </p>

    <!-- Toolbar is the set of controls for copying the command output,
    saving and deleting presets. -->
    <ToolbarComponent />

    <!-- JSON formatted viewer so the user can view or copy the configured
    JSON output for their generated commands. -->
    <JsonViewerComponent />
  </div>
</template>

<script setup lang="ts">
import AudioComponent from './AudioComponent.vue'
import CommandComponent from './CommandComponent.vue'
import FileIOComponent from './FileIOComponent.vue'
import FiltersComponent from './FiltersComponent.vue'
import FormatComponent from './FormatComponent.vue'
import JsonViewerComponent from './JsonViewerComponent.vue'
import OptionsComponent from './OptionsComponent.vue'
import PresetsComponent from './PresetsComponent.vue'
import ToolbarComponent from './ToolbarComponent.vue'
import VideoComponent from './VideoComponent.vue'

// const preset = reactive<Preset>({
//   id: 'custom',
//   name: null,
// })

// const defaultForm = reactive({})

// const controls = reactive({
//   showJSON: false,
// })

// const generateCommand = () => {
//   return formStore.command
// }

// const updateOutput = () => {
//   if (formStore.io.output) {
//     const { format, io } = formStore
//     const ext = util.extname(io.output)
//     if (ext) {
//       formStore.io.output = `${io.output.replace(ext, `.${format.container}`)}`
//     }
//   }
// }

// const route = useRoute()
// const router = useRouter()

// const setDataFromQueryParams = () => {
//   const { query } = route
//   formStore.fromQueryParams(query as Record<string, string>)
// }

// const updateQueryParams = () => {
//   const params = formStore.queryParams
//   router.push({ query: params }).catch(() => {})
// }

// const reset = () => {
//   Object.assign(formStore, clone(defaultForm))
//   preset.id = 'custom'
//   preset.name = null
// }

// const toggleJSON = () => {
//   controls.showJSON = !controls.showJSON
// }

// onMounted(() => {
//   generateCommand()
//   Object.assign(defaultForm, clone(formStore))
//   setDataFromQueryParams()
// })

// watch(
//   () => formStore,
//   () => {
//     updateOutput()
//     generateCommand()
//     updateQueryParams()
//   },
//   { deep: true },
// )

// watch(
//   () => preset,
//   () => {
//     if (preset.id.startsWith('preset-')) {
//       // const presetData = presets.getPresetFromLocalStorage(preset.id)
//       // Object.assign(form, merge(form, presetData.data))
//       // preset.name = presetData.name
//     } else if (preset.id !== 'custom' && !preset.id.startsWith('preset-')) {
//       // setPreset(preset.id)
//       // preset.name = null
//     }
//   },
// )
</script>

<style scoped>
.disclaimer {
  font-style: italic;
  font-size: 0.8em;
  padding-top: 6px;
}
.protocol {
  flex: 0 0 20% !important;
}
.hidden-cmd {
  opacity: 0;
  height: 0;
}
.hidden-cmd textarea {
  height: 0;
}
</style>
