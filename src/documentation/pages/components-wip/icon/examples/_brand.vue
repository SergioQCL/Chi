<template lang="pug">
  <ComponentExample title="Brand" titleSize="h4" id="brand" padding="-p--0" :tabs="exampleTabs">
    p.-text(slot="example-description")
      | Brand icon colors reinforce Lumen's brand.
    .chi-grid.-no-gutter(slot="example")
      .chi-col.-w--12.-w-md--6.-p--1.-d--flex.-justify-content--center
        div(v-for="color in colors" :class="`chi-icon -${color} -m--1`")
          svg
            use(xlink:href='#icon-atom')
      .chi-col.-w--12.-w-md--6.-bg--black.-p--1.-d--flex.-justify-content--center
        each color in ['icon--secondary', 'icon--light']
          if (color === 'icon--secondary')
            div(class=`chi-icon -icon--secondary -m--1`)
              svg
                use(xlink:href='#icon-atom')
          else if (color === 'icon--light')
            div(class=`chi-icon -icon--light -m--1`)
              svg
                use(xlink:href='#icon-atom')
    <pre class="language-html" slot="code-webcomponent">
      <code v-highlight="$data.codeSnippets.webcomponent" class="html"></code>
    </pre>
    <pre class="language-html" slot="code-htmlblueprint">
      <code v-highlight="$data.codeSnippets.htmlblueprint" class="html"></code>
    </pre>
  </ComponentExample>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
  data: () => {
    return {
      exampleTabs: [
        {
          active: true,
          id: 'webcomponent',
          label: 'Web component',
        },
        {
          id: 'htmlblueprint',
          label: 'HTML blueprint',
        },
      ],
      colors: ['', 'icon--primary', 'icon--dark', 'icon--grey'],
      codeSnippets: {
        webcomponent: `<!-- For light backgrounds -->
<chi-icon icon="atom"></chi-icon>
<chi-icon icon="atom" color="primary"></chi-icon>
<chi-icon icon="atom" color="dark"></chi-icon>
<chi-icon icon="atom" color="grey"></chi-icon>
<!-- For dark backgrounds -->
<chi-icon icon="atom" color="secondary"></chi-icon>
<chi-icon icon="atom" color="light"></chi-icon>`,
        htmlblueprint: `<!-- For light backgrounds -->
<i class="chi-icon icon-atom" aria-hidden="true"></i>
<i class="chi-icon icon-atom -icon--primary" aria-hidden="true"></i>
<i class="chi-icon icon-atom -icon--dark" aria-hidden="true"></i>
<i class="chi-icon icon-atom -icon--grey" aria-hidden="true"></i>
<!-- For dark backgrounds -->
<i class="chi-icon icon-atom -icon--secondary" aria-hidden="true"></i>
<i class="chi-icon icon-atom -icon--light" aria-hidden="true"></i>`,
      },
    };
  },
})
export default class Brand extends Vue {}
</script>
