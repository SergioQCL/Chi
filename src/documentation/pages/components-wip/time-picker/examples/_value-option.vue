<template lang="pug">
  <ComponentExample titleSize="h4" title="Value option" id="value-option" :tabs="exampleTabs">
    .chi-form__item(style="max-width: 14rem;" slot="example")
      chi-label(for='unique-id-va1') Time
      chi-time-picker#unique-id-va1(value='09:00')
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
          disabled: true,
          id: 'htmlblueprint',
          label: 'HTML blueprint'
        }
      ],
      codeSnippets: {
        webcomponent: `<chi-label for="unique-id-va1">Time</chi-label>
<chi-time-picker id="unique-id-va1" value="09:00"></chi-time-picker>`,
        htmlblueprint: ``
      }
    };
  }
})
export default class ValueOption extends Vue {}
</script>
