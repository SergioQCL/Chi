<template lang="pug">
  <ComponentExample title="Left + Right Aligned" id="left-right-aligned-portal" :tabs="exampleTabs">
    .chi-grid(slot="example")
      .chi-col.-w--12.-w-sm--8.-w-md--6.-w-lg--5
        .chi-form__item
          chi-label(for="example__portal-icon-left-right-aligned") Label
          chi-text-input(
            icon-left='search',
            icon-right='check',
            value="Sample Text"
            id="example__portal-icon-left-right-aligned"
          )
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
          label: 'Web component'
        },
        {
          id: 'htmlblueprint',
          label: 'HTML blueprint'
        }
      ],
      codeSnippets: {
        webcomponent: `<div class="chi-form__item">
  <chi-label for="example__portal-icon-left-right-aligned">Label</chi-label>
  <chi-text-input icon-left="search" icon-right="check" value="Sample Text" id="example__portal-icon-left-right-aligned"></chi-text-input>
</div>`,
        htmlblueprint: `<div class="chi-form__item">
  <label class="chi-label" for="example__portal-icon-left-right-aligned">Label</label>
  <div class="chi-input__wrapper -icon--left -icon--right">
    <input type="text" class="chi-input" value="Sample text" id="example__portal-icon-left-right-aligned">
    <i class="chi-icon icon-search" aria-hidden="true"></i>
    <i class="chi-icon icon-check" aria-hidden="true"></i>
  </div>
</div>`
      }
    };
  }
})
export default class LeftRightAlignedPortal extends Vue {}
</script>
