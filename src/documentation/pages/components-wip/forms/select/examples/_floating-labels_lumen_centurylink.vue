<template lang="pug">
  <ComponentExample title="Floating labels" id="floating-labels-lumen-centurylink" :tabs="exampleTabs">
    p.-text(slot="example-description") 
      | Floating labels are a solution to keep the placeholder visible when no label is attached to the select. 
      | Chi only supports floating labels on <code>-lg</code> and <code>-xl</code> selects.
    <Wrapper slot="example">
      .chi-col.-w--12.-p--2(v-for="size in sizes")
        .chi-input__wrapper.-floating-label(style="max-width:20rem" :ref="`label-${size}`")
          select(:class="`chi-select -${size}`" :id="`floating-label-select-${size}`")
            option
            option Option 1
            option Option 2
            option Option 3
          label(:for="`floating-label-select-${size}`") Placeholder text
    </Wrapper>
    <pre class="language-html" slot="code-webcomponent">
      <code v-highlight="$data.codeSnippets.webcomponent" class="html"></code>
    </pre>   
    <Wrapper slot="code-htmlblueprint">
      <JSNeeded />
      <pre class="language-html">
        <code v-highlight="$data.codeSnippets.htmlblueprint" class="html"></code>
      </pre>
    </Wrapper>
  </ComponentExample>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

declare const chi: any;

@Component({
  data: () => {
    return {
      exampleTabs: [
        {
          disabled: true,
          id: 'webcomponent',
          label: 'Web component'
        },
        {
          active: true,
          id: 'htmlblueprint',
          label: 'HTML blueprint'
        }
      ],
      codeSnippets: {
        webcomponent: ``,
        htmlblueprint: `<div id="floating-label-lg" class="chi-input__wrapper -floating-label">
  <select class="chi-select -lg" id="floating-label-select-lg">
    <option></option>
    <option>Option 1</option>
    <option>Option 2</option>
    <option>Option 3</option>
  </select>
  <label for="floating-label-select-lg">Placeholder text</label>
</div>

<div id="floating-label-xl" class="chi-input__wrapper -floating-label">
  <select class="chi-select -xl" id="floating-label-select-xl">
    <option></option>
    <option>Option 1</option>
    <option>Option 2</option>
    <option>Option 3</option>
  </select>
  <label for="floating-label-select-xl">Placeholder text</label>
</div>

<script>chi.floatingLabel(document.querySelectorAll('.-floating-label'));<\/script>`
      }
    };
  }
})
export default class FloatingLabelsLumenCenturyLink extends Vue {
  floatingLabels: any[] = [];
  sizes = ['lg', 'xl'];

  mounted() {
    this.sizes.forEach((size: string) => {
      this.floatingLabels.push(chi.floatingLabel(this.$refs[`label-${size}`]));
    });
  }

  beforeDestroy() {
    this.floatingLabels.forEach((floatingLabel: any) => {
      floatingLabel[0].dispose();
    });
  }
}
</script>
