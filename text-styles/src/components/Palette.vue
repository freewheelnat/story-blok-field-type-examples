<script>
import Swatch from './Swatch'



export default {
  props: {
    setValue: {
      type: Function,
      default: () => undefined,
    },
    value: {
      type: String,
      required: false,
      default: undefined,
    },
    textStyles: {
      type: Array,
    },
  },
  render() {
    const { columns, textStyles, value, setValue } = this

    return (
      <div
        class="plugin-swatch-grid"
        style={`grid-template-columns: repeat(${columns}, 1fr)`}
      >
        {textStyles.map((textStyle) => (
          <Swatch
            textStyleName={textStyle.name}
            textStyleCategory={textStyle.category}
            textStylePath={ textStyle.path}
            selected={textStyle.name === value}
            setValue={setValue}
          />
        ))}
      </div>
    )
  },
}
</script>

<style scoped lang="scss">
.plugin-swatch-grid {
  display: flex;
  flex-wrap: wrap;
  //justify-items: start;
  //width: auto;
}
</style>