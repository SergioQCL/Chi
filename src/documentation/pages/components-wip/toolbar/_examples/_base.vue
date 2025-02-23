<template lang="pug">
  <ComponentExample title="Base" id="base" :tabs="exampleTabs">
    chi-data-table-toolbar(slot="example")
      template(v-slot:start)
        chi-search-input(:data-table-search='true')
        .chi-divider.-vertical
        chi-data-table-views(:views='toolbar.viewsData')
        .chi-divider.-vertical
        chi-data-table-filters.-ml--2(:filters-data='toolbar.filtersData', :custom-items='toolbar.customItemsData')
          template(v-slot:custom-one)
            .chi-form__item
              chi-label(for='input-1') City
              chi-text-input#input-1
              chi-label(for='input-2') Zip Code
              chi-text-input#input-2
          template(v-slot:custom-two)
            chi-date-picker
      template(v-slot:end)
        chi-column-customization(:columns-data='toolbar.columnsData')
    <pre class="language-html" slot="code-webcomponent">
      <code v-highlight="$data.codeSnippets.webcomponent" class="html"></code>
    </pre>
    <Wrapper slot="code-vue">
      .chi-tab__description
        | Use the slots <code>start</code> to add elements to the left side area of the Toolbar Header and the <code>end</code> - to the right side.
      <pre class="language-html">
        <code v-highlight="$data.codeSnippets.vue" class="html"></code>
      </pre>
    </Wrapper>
    <Wrapper slot="code-htmlblueprint">
      .chi-tab__description
        | To render toolbar, use the class <code>chi-toolbar</code>.
      <pre class="language-html">
        <code v-highlight="$data.codeSnippets.htmlblueprint" class="html"></code>
      </pre>
    </Wrapper>
  </ComponentExample>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

const customItems = [
  {
    template: 'custom-one',
    label: 'Custom 1'
  },
  {
    template: 'custom-two',
    label: 'Custom 2'
  }
];
const filters = [
  {
    name: 'status',
    type: 'select',
    id: 'myoption1',
    label: 'Selector',
    options: [
      {
        label: 'Active',
        value: 'active'
      },
      {
        label: 'Inactive',
        value: 'inactive'
      }
    ],
    value: 'active'
  },
  {
    name: 'input',
    placeholder: 'Input filter',
    type: 'input',
    value: '',
    id: 'myoption2',
    label: 'Input Filter'
  },
  {
    name: 'checkbox',
    type: 'checkbox',
    checked: false,
    id: 'myoption3',
    label: 'Checkbox'
  },
  {
    name: 'statusAdvanced',
    label: 'Status',
    type: 'select',
    id: 'myoption4',
    options: [
      {
        label: 'Active',
        value: 'active',
        selected: false
      },
      {
        label: 'Inactive',
        value: 'inactive',
        selected: false
      }
    ],
    advanced: true,
    value: 'active'
  },
  {
    name: 'inputAdvanced',
    label: 'Label',
    id: 'myoption5',
    advanced: true
  },
  {
    name: 'textareaAdvanced',
    label: 'textarea',
    id: 'myoption6',
    type: 'textarea',
    advanced: true
  },
  {
    name: 'checkboxAdvanced',
    id: 'myoption7',
    label: 'Advanced Checkbox',
    type: 'checkbox',
    advanced: true
  }
];
const columns = [
  {
    name: 'columnA',
    label: 'Column A'
  },
  {
    name: 'columnB',
    label: 'Column B'
  },
  {
    name: 'columnC',
    label: 'Column C',
    locked: true,
    selected: true
  },
  {
    name: 'columnD',
    label: 'Column D',
    locked: true,
    selected: true
  },
  {
    name: 'columnE',
    label: 'Column E',
    selected: true
  },
  {
    name: 'columnF',
    label: 'Column F',
    selected: true
  },
  {
    name: 'columnG',
    label: 'Column G'
  },
  {
    name: 'columnH',
    label: 'Column H'
  },
  {
    name: 'columnI',
    label: 'Column I'
  },
  {
    name: 'columnJ',
    label: 'Column J'
  }
];

@Component({
  data: () => {
    return {
      toolbar: {
        customItemsData: customItems,
        filtersData: filters,
        columnsData: {
          columns: columns
        },
        viewsData: [
          {
            id: 'view-1',
            label: 'View 1',
            columns: columns,
            searchString: 'abc',
            filters: filters
          },
          {
            id: 'view-2',
            label: 'View 2',
            columns: [],
            searchString: 'abcde',
            filters: []
          }
        ]
      },
      exampleTabs: [
        {
          disabled: true,
          id: 'webcomponent',
          label: 'Web component'
        },
        {
          active: true,
          id: 'vue',
          label: 'Vue'
        },
        {
          id: 'htmlblueprint',
          label: 'HTML blueprint'
        }
      ],
      codeSnippets: {
        webcomponent: ``,
        vue: `<!-- Vue component -->
<ChiDataTableToolbar>
  <template v-slot:start>
    <ChiSearchInput :dataTableSearch="true" />
    <div class="chi-divider -vertical"></div>
    <!-- To render views, use Views sub-module of Toolbar -->
    <ChiDataTableViews :views="toolbar.viewsData" />
    <div class="chi-divider -vertical"></div>
    <!-- To render filters, use Filters sub-module of Toolbar by providing it with respective data -->
    <ChiDataTableFilters :filtersData="toolbar.filtersData" :customItems="toolbar.customItemsData" class="-ml--2">
      <template v-slot:customAdvanced>
        <div class="chi-form__item">
          <chi-label for="input-1">City</chi-label>
          <chi-text-input id="input-1" @chiChange="e => inputOneChangeHandler(e)"></chi-text-input>
          <chi-label for="input-2">Zip Code</chi-label>
          <chi-text-input id="input-2" @chiChange="e => inputTwoChangeHandler(e)"></chi-text-input>
        </div>
      </template>
      <template v-slot:customAdvanced2>
        <chi-date-picker @chiDateChange="e => dateChangeHandler(e)" />
      </template>
    </ChiDataTableFilters>
  </template>
  <template v-slot:end>
    <!-- To enable customization of columns, use Column Customization sub-module of Toolbar by providing it with respective data -->
    <ChiColumnCustomization :columnsData="toolbar.columnsData" />
  </template>
</ChiDataTableToolbar>

<!-- Example Data -->
data: () => {
  const customItems = [
    {
      template: 'customAdvanced',
      label: 'Custom 1',
    },
    {
      template: 'customAdvanced2',
      label: 'Custom 2',
    },
  ];
  const filters = [
    {
      name: 'status',
      type: 'select',
      id: 'myoption1',
      label: 'Selector',
      options: [
        {
          label: 'Active',
          value: 'active',
        },
        {
          label: 'Inactive',
          value: 'inactive',
        },
      ],
      value: 'active',
    },
    {
      name: 'input',
      placeholder: 'Input filter',
      type: 'input',
      value: '',
      id: 'myoption2',
      label: 'Input Filter',
    },
    {
      name: 'checkbox',
      type: 'checkbox',
      checked: false,
      id: 'myoption3',
      label: 'Checkbox',
    },
    {
      name: 'statusAdvanced',
      label: 'Status',
      type: 'select',
      id: 'myoption4',
      options: [
        {
          label: 'Active',
          value: 'active',
          selected: false,
        },
        {
          label: 'Inactive',
          value: 'inactive',
          selected: false,
        },
      ],
      advanced: true,
      value: 'active',
    },
    {
      name: 'inputAdvanced',
      label: 'Label',
      id: 'myoption5',
      advanced: true,
    },
    {
      name: 'textareaAdvanced',
      label: 'textarea',
      id: 'myoption6',
      type: 'textarea',
      advanced: true,
    },
    {
      name: 'checkboxAdvanced',
      id: 'myoption7',
      label: 'Advanced Checkbox',
      type: 'checkbox',
      advanced: true,
    },
  ];
  const columns = [
    {
      name: 'columnA',
      label: 'Column A',
    },
    {
      name: 'columnB',
      label: 'Column B',
    },
    {
      name: 'columnC',
      label: 'Column C',
      locked: true,
      selected: true,
    },
    {
      name: 'columnD',
      label: 'Column D',
      locked: true,
      selected: true,
    },
    {
      name: 'columnE',
      label: 'Column E',
      selected: true,
    },
    {
      name: 'columnF',
      label: 'Column F',
      selected: true,
    },
    {
      name: 'columnG',
      label: 'Column G',
    },
    {
      name: 'columnH',
      label: 'Column H',
    },
    {
      name: 'columnI',
      label: 'Column I',
    },
    {
      name: 'columnJ',
      label: 'Column J',
    },
  ];

  return {
    toolbar: {
      customItemsData: customItems,
      filtersData: filters,
      columnsData: {
        columns: columns
      },
      viewsData: [
        {
          id: 'view-1',
          label: 'View 1',
          columns: columns,
          searchString: 'abc',
          filters: filters
        },
        {
          id: 'view-2',
          label: 'View 2',
          columns: [],
          searchString: 'abcde',
          filters: [],
        },
      ],
    };
  };
};`,
        htmlblueprint: `<div class="chi-toolbar">
  <div class="chi-toolbar__header">
    <div class="chi-toolbar__start">
      <div class="chi-toolbar__search">
        <div class="chi-form__item">
            <chi-search-input id="example__base"></chi-search-input>
        </div>
      </div>
      <div class="chi-divider -vertical"></div>
      <div class="chi-toolbar__views">
        <div class="chi-toolbar__views-desktop">
          <div class="chi-form__item">
            <select class="chi-select" id="example-views-1">
              <option>View 1</option>
              <option>View 2</option>
            </select>
          </div>
        </div>
      </div>
      <div class="chi-divider -vertical"></div>
      <div class="chi-toolbar__filters">
        <div class="chi-toolbar__filters-desktop">
          <div class="chi-form__item">
            <select class="chi-select" id="example-ba1">
              <option value="">Select</option>
              <option>Option 1</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
          </div>
          <div class="chi-form__item">
            <select class="chi-select" id="example-ba2">
              <option value="">Select</option>
              <option>Option 1</option>
              <option>Option 2</option>
              <option>Option 3</option>
            </select>
          </div>
          <button class="chi-button -icon -flat" id="button-b-filters" aria-label="Filters" data-tooltip="Filters" data-position="top">
            <div class="chi-button__content">
              <i class="chi-icon icon-filter" aria-hidden="true"></i>
            </div>
          </button>
        </div>
        <div class="chi-toolbar__filters-mobile">
          <button class="chi-button -icon -flat chi-drawer__trigger" id="drawer-trigger-b1" data-target="#drawer-1" aria-label="Button action">
            <div class="chi-button__content">
              <i class="chi-icon icon-filter" aria-hidden="true"></i>
            </div>
          </button>
        </div>
      </div>
    </div>
    <div class="chi-toolbar__end">
      <div class="chi-toolbar__actions">
        <div class="chi-toolbar__actions-desktop">
          <button class="chi-button -icon -flat" id="button-b-download" aria-label="Download" data-tooltip="Download" data-position="top">
            <div class="chi-button__content">
              <i class="chi-icon icon-arrow-to-bottom" aria-hidden="true"></i>
            </div>
          </button>
          <button class="chi-button -icon -flat" id="button-b-refresh" aria-label="Refresh" data-tooltip="Refresh" data-position="top">
            <div class="chi-button__content">
              <i class="chi-icon icon-refresh" aria-hidden="true"></i>
            </div>
          </button>
          <button class="chi-button -icon -flat" id="button-b-column-customization" aria-label="Column Customization" data-tooltip="Column Customization" data-position="top">
            <div class="chi-button__content">
              <i class="chi-icon icon-table-column-settings" aria-hidden="true"></i>
            </div>
          </button>
        </div>
        <div class="chi-toolbar__actions-mobile">
          <button class="chi-button -icon -flat chi-drawer__trigger" id="drawer-trigger-b2" data-target="#drawer-2" aria-label="Button action">
            <div class="chi-button__content">
              <i class="chi-icon icon-more-vert" aria-hidden="true"></i>
            </div>
          </button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Drawer -->
<div class="chi-backdrop -closed">
  <div class="chi-backdrop__wrapper">
    <div class="chi-drawer -left -menu -position--absolute" id="drawer-1">
      <div class="chi-drawer__header">
        <span class="chi-drawer__title">Filters</span>
        <button class="chi-button -icon -close" aria-label="Close">
          <div class="chi-button__content">
            <i class="chi-icon icon-x" aria-hidden="true"></i>
          </div>
        </button>
      </div>
      <div class="chi-drawer__content -px--2 -py--3">
        <div class="chi-form__item -mb--2">
          <label class="chi-label" for="example-ba11">Label</label>
          <select class="chi-select" id="example-ba11">
            <option value="">Select</option>
            <option>Option 1</option>
            <option>Option 2</option>
            <option>Option 3</option>
          </select>
        </div>
        <div class="chi-form__item -mb--2">
          <label class="chi-label" for="example-ba12">Label</label>
          <select class="chi-select" id="example-ba12">
            <option value="">Select</option>
            <option>Option 1</option>
            <option>Option 2</option>
            <option>Option 3</option>
          </select>
        </div>
        <div class="chi-form__item -mb--2">
          <label class="chi-label" for="example-ba13">Label</label>
          <select class="chi-select" id="example-ba13">
            <option value="">Select</option>
            <option>Option 1</option>
            <option>Option 2</option>
            <option>Option 3</option>
          </select>
        </div>
        <div class="chi-form__item -mb--2">
          <label class="chi-label" for="example-ba14">Label</label>
          <select class="chi-select" id="example-ba14">
            <option value="">Select</option>
            <option>Option 1</option>
            <option>Option 2</option>
            <option>Option 3</option>
          </select>
        </div>
      </div>
      <div class="-d--flex -justify-content--center -pb--2">
        <button class="chi-button -primary">Apply</button>
        <button class="chi-button -ml--2">Cancel</button>
      </div>
    </div>
  </div>
</div>
<div class="chi-backdrop -closed">
  <div class="chi-backdrop__wrapper">
    <div class="chi-drawer -right -menu -position--absolute" id="drawer-2">
      <div class="chi-drawer__header">
        <span class="chi-drawer__title">Actions</span>
        <button class="chi-button -icon -close" aria-label="Close">
          <div class="chi-button__content">
            <i class="chi-icon icon-x" aria-hidden="true"></i>
          </div>
        </button>
      </div>
      <div class="chi-drawer__content -px--2">
        <ul class="-no-style">
          <li class="-text--md">Download data</li>
          <div class="chi-divider"></div>
          <li class="-text--md">Refresh results</li>
          <div class="chi-divider"></div>
        </ul>
      </div>
    </div>
  </div>
</div>

<!-- Javascript -->
<script>
  chi.drawer(document.getElementById('drawer-trigger-b1'));
  chi.drawer(document.getElementById('drawer-trigger-b2'));
  chi.tooltip(document.querySelectorAll('[data-tooltip]'));
<\/script>`
      }
    };
  }
})
export default class Base extends Vue {}
</script>
