<template lang="pug">
  <ComponentExample title="Complex combination" id="complex-combination" additionalClasses="-p-lg--6" :tabs="exampleTabs">
    div(slot="example")
      button.chi-button(@click="toggleSkeletonVisibility") Toggle Skeleton
      .complex-combination-skeleton(v-if="isSkeletonVisible")
        .-mw--480
          .chi-skeleton.-mt--2.-w--90
          .-mt--2
            .chi-skeleton.-xs.-mt--1
            .chi-skeleton.-xs.-mt--1.-w--90
            .chi-skeleton.-xs.-mt--1.-w--50
          .-d--flex.-mt--4
            .chi-skeleton.-circle
            .chi-skeleton.-rounded.-flex--grow1.-ml--2
            .chi-skeleton.-rounded.-ml--2.-w--15   
      .complex-combination-html(v-else)
        .-text--h2 Lorem ipsum dolor sit amet
        p.-mw--480
          | Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
          | eiusmod tempor incididunt ut labore et dolore magna aliqua.
          | Ut enim ad minim veniam, quis nostrud exercitation.
        .-d--flex.-mw--480.-mt--4
          .chi-avatar
            i.chi-icon.icon-user(aria-hidden="true")
          .chi-form__item.-flex--grow1.-ml--2
            input.chi-input(type='text' placeholder='Placeholder' aria-label='Example input')
          button.chi-button.-primary.-ml--2 Send
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
        htmlblueprint: `<div class="-mw--480">
  <div class="chi-skeleton -mt--2 -w--90"></div>
  <div class="-mt--2">
    <div class="chi-skeleton -xs -mt--1"></div>
    <div class="chi-skeleton -xs -mt--1 -w--90"></div>
    <div class="chi-skeleton -xs -mt--1 -w--50"></div>
  </div>
  <div class="-d--flex -mt--4">
    <div class="chi-skeleton -circle"></div>
    <div class="chi-skeleton -rounded -flex--grow1 -ml--2"></div>
    <div class="chi-skeleton -rounded -ml--2 -w--15"></div>
  </div>
</div>`
      }
    };
  }
})
export default class ComplexCombination extends Vue {
  isSkeletonVisible = true;

  toggleSkeletonVisibility() {
    this.isSkeletonVisible = !this.isSkeletonVisible;
  }
}
</script>
