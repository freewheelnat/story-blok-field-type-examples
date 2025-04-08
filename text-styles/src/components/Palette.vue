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
        {textStyles.map((textStyleCategory) => (
          <div class = "plugin-swatch-category">
            <div >{textStyleCategory.category}</div>
            {textStyleCategory.styles.map((textStyle) => (
              <Swatch
                textStyleName={textStyle.name}
                textStyleCategory={textStyle.category}
                textStylePath={textStyle.path}
                selected={textStyle.name === value}
                setValue={setValue}
              />))}
          </div>
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
}
.plugin-swatch-category {
  padding-bottom: 20px;
}
</style>