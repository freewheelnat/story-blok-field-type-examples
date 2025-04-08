<script>
import Checkmark from '@/components/Checkmark'

export default {
  name: 'Swatch',
  props: {
    textStyleCategory: {
      type: String,
      required: true,
    },
    textStyleName: {
      type: String,
      required: true,
    },
    textStylePath: {
      type: String,
      required: true,
    },
    selected: {
      type: Boolean,
      required: false,
      default: false,
    },
    setValue: {
      type: Function,
      default: () => undefined,
    },
  },
  render() {
    const { textStyleName, textStylePath, selected, setValue } = this
    return (
      <div
        class={`plugin-swatch ${
          selected ? 'plugin-swatch--selected' : ''
          }`}
        
      >
        <div
          class="plugin-swatch__button"
          onClick={() =>
            this.selected ? setValue(undefined) : setValue(textStyleName)
          }
        >
          <img class="plugin-swatch__image"  src={textStylePath} />
          {selected && <Checkmark class="plugin-swatch__checkmark" />}
        </div>
      </div>
    )
  },
}
</script>

<style scoped lang="scss">

.plugin-swatch {
}

.plugin-swatch__button {
  cursor: pointer;
  position: relative;
  display: inline-block;
}

.plugin-swatch__image {
  display: block;
  width: 100%;
}

.plugin-swatch__checkmark {
  position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 60px;
    height: auto;
}
</style>
