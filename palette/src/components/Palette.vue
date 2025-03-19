<script>
import Swatch from './Swatch'



const defaultColors = [
  { colour: '#00B3B0', name: "name 1" },
  { colour: '#40C6C4', name: "name 2" },
  { colour: '#7FD9D7', name: "name 3" },
  { colour: '#D9F4F3', name: "name 4"},
  { colour: '#1B243F', name: "name 5" },
  { colour: '#545B6F', name: "name 6" },
  { colour: '#8D919F', name: "name 7" },
  { colour: '#C6C8CF', name: "name 8" },
  { colour: '#B1B5BE', name: "name 9" },
  { colour: '#DFE3E8', name: "name 10" },
  { colour: '#E7EAEE', name: "name 11" },
  { colour: '#EFF1F3', name: "name 12" },
  { colour: '#2DB47D', name: "name 13" },
  { colour: '#62C79E', name: "name 14" },
  { colour: '#96D9BE', name: "name 15" },
  { colour: '#CAECDE', name: "name 16" },
  { colour: '#395ECE', name: "name 17" },
  { colour: '#6B87DB', name: "name 18" },
  { colour: '#9CAEE6', name: "name 19" },
  { colour: '#CDD7F3', name: "name 20" },
]

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
    size: {
      // small, medium, large
      type: String,
      default: 'medium',
      validator(value) {
        return ['small', 'medium', 'large'].includes(value)
      },
    },
    background: {
      type: String,
      default: '#00000000',
    },
    colors: {
      type: Array,
      default: defaultColors,
    },
  },
  render() {
    const { columns, colors, background, size, value, setValue } = this

    return (
      <div
        class="plugin-swatch-grid"
        style={`grid-template-columns: repeat(${columns}, 1fr)`}
      >
        {colors.map((color) => (
          <Swatch
            color={color.colour}
            background={background}
            colorName={color.name}
            size={size}
            selected={color.name === value}
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