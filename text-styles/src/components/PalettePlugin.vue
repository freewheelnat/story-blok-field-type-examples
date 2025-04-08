<script>
import Palette from '@/components/Palette'

const messiTextStyles = [
  { category: 'heading', name: 'Heading XL', path: 'https://a.storyblok.com/f/187111/1008x61/d24de7830a/headingxl.png' },
  { category: 'heading', name: 'Heading XL Bold', path: 'https://a.storyblok.com/f/187111/1008x61/e9cf8b5a45/headingxlbold.png' },
  { category: 'heading', name: 'Heading L', path: 'https://a.storyblok.com/f/187111/1008x56/daebc723a8/headingl.png' },
  { category: 'heading', name: 'Heading L Bold', path: 'https://a.storyblok.com/f/187111/1008x56/20c800917e/headinglbold.png' },
  { category: 'heading', name: 'Heading M', path: 'https://a.storyblok.com/f/187111/1008x56/45c53c28f3/headingm.png' },
  { category: 'heading', name: 'Heading M Bold', path: 'https://a.storyblok.com/f/187111/1008x56/4a2104cbbe/headingmbold.png' },
  { category: 'heading', name: 'Heading S Bold', path: 'https://a.storyblok.com/f/187111/1008x52/22215faccf/headingsbold.png' },
  { category: 'body', name: 'Body M', path: 'https://a.storyblok.com/f/187111/1008x56/8e2f0d4ba6/bodym.png' },
  { category: 'body', name: 'Body M Italic', path: 'https://a.storyblok.com/f/187111/1008x56/56cf3d49db/bodymitalic.png' },
  { category: 'body', name: 'Body M Bold', path: 'https://a.storyblok.com/f/187111/1008x56/711748f4ed/bodymbold.png' },
  { category: 'body', name: 'Body S', path: 'https://a.storyblok.com/f/187111/1008x52/c06187126d/bodys.png' },
  { category: 'body', name: 'Body S Italic', path: 'https://a.storyblok.com/f/187111/1008x52/494552e945/bodysitalic.png' },
  { category: 'body', name: 'Body S Bold', path: 'https://a.storyblok.com/f/187111/1008x52/7d6af1ae7c/bodysbold.png' },
  { category: 'body', name: 'Body XS', path: 'https://a.storyblok.com/f/187111/1008x51/6d8eeda7fa/bodyxs.png' },
  { category: 'body', name: 'Body XS Italic', path: 'https://a.storyblok.com/f/187111/1008x51/240a82488e/bodyxsitalic.png' },
  { category: 'body', name: 'Body XS Bold', path: 'https://a.storyblok.com/f/187111/1008x51/5f69f82b2c/bodyxsbold.png' }
]

const messiTextStyles2 = [
  {
    category: 'heading', styles: [{ name: 'Heading XL', path: 'https://a.storyblok.com/f/187111/1008x61/d24de7830a/headingxl.png' },
    { name: 'Heading XL Bold', path: 'https://a.storyblok.com/f/187111/1008x61/e9cf8b5a45/headingxlbold.png' },
    { name: 'Heading L', path: 'https://a.storyblok.com/f/187111/1008x56/daebc723a8/headingl.png' },
    { name: 'Heading L Bold', path: 'https://a.storyblok.com/f/187111/1008x56/20c800917e/headinglbold.png' },
    {  name: 'Heading M', path: 'https://a.storyblok.com/f/187111/1008x56/45c53c28f3/headingm.png' },
    {  name: 'Heading M Bold', path: 'https://a.storyblok.com/f/187111/1008x56/4a2104cbbe/headingmbold.png' },
    {  name: 'Heading S Bold', path: 'https://a.storyblok.com/f/187111/1008x52/22215faccf/headingsbold.png' }]
  },
    {
    category: 'body', styles: [{ name: 'Body M', path: 'https://a.storyblok.com/f/187111/1008x56/8e2f0d4ba6/bodym.png' },
    { category: 'body', name: 'Body M Italic', path: 'https://a.storyblok.com/f/187111/1008x56/56cf3d49db/bodymitalic.png' },
    { category: 'body', name: 'Body M Bold', path: 'https://a.storyblok.com/f/187111/1008x56/711748f4ed/bodymbold.png' },
    { category: 'body', name: 'Body S', path: 'https://a.storyblok.com/f/187111/1008x52/c06187126d/bodys.png' },
    { category: 'body', name: 'Body S Italic', path: 'https://a.storyblok.com/f/187111/1008x52/494552e945/bodysitalic.png' },
    { category: 'body', name: 'Body S Bold', path: 'https://a.storyblok.com/f/187111/1008x52/7d6af1ae7c/bodysbold.png' },
    { category: 'body', name: 'Body XS', path: 'https://a.storyblok.com/f/187111/1008x51/6d8eeda7fa/bodyxs.png' },
    { category: 'body', name: 'Body XS Italic', path: 'https://a.storyblok.com/f/187111/1008x51/240a82488e/bodyxsitalic.png' },
    { category: 'body', name: 'Body XS Bold', path: 'https://a.storyblok.com/f/187111/1008x51/5f69f82b2c/bodyxsbold.png' }]
  }
]


export default {
  props: {
    options: {
      type: Object,
      default: undefined,
    },
    setValue: {
      type: Function,
      default: () => undefined,
    },
    value: {
      type: Object,
      default: undefined,
    },
  },
  created() {
    const defaultValue = this.options.defaultValue
    if (!this.value?.value) {
      this.setValue({ value: defaultValue })
    }
  },
  render() {
    const defaultValue = this.options.defaultValue
    return (
      <Palette
        setValue={(value) => this.setValue({ value })}
        value={this.value?.value ?? defaultValue}
        textStyles={messiTextStyles}
      />
    )
  },
}
</script>

<style scoped lang="scss">
</style>