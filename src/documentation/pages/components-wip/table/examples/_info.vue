<template lang="pug">
  <ComponentExample titleSize="h4" title="Info" id="info" :tabs="exampleTabs">
    p.-text(slot="example-description")
      | Render an info state by applying the modifier class <code>-row--info</code>.
    table.chi-table(slot="example")
      thead
        tr.-row--info 
          th Name
          th ID
          th Last Login
      tbody
        tr(v-for="(row, index) in rows" :key="index" :class="{'-row--info': index === 1}")
          td {{ row.cell1 }}
          td {{ row.cell2 }}
          td {{ row.cell3 }}
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
      rows: [
        { cell1: 'Name 1', cell2: 'name-1', cell3: 'Dec 18, 2020 3:26 PM' },
        { cell1: 'Name 2', cell2: 'name-2', cell3: 'Dec 18, 2020 2:38 AM' },
        { cell1: 'Name 3', cell2: 'name-3', cell3: 'Nov 5, 2020 10:15 AM' }
      ],
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
        htmlblueprint: `<table class="chi-table">
    <thead>
        <tr class="-row--info">
            <th>Name</th>
            <th>ID</th>
            <th>Last Login</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Name 1</td>
            <td>name-1</td>
            <td>Dec 18, 2020 3:26 PM</td>
        </tr>
        <tr class="-row--info">
            <td>Name 2</td>
            <td>name-2</td>
            <td>Dec 18, 2020 2:38 AM</td>
        </tr>
        <tr>
            <td>Name 3</td>
            <td>name-3</td>
            <td>Nov 5, 2020 10:15 AM</td>
        </tr>
    </tbody>
</table>`
      }
    };
  }
})
export default class Info extends Vue {}
</script>
