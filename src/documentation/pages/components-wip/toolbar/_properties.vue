<template lang="pug">
  div
    h2 Chi Vue
    h3 Props
    h4 Search Input
    p.-text
      | Please visit Search input dedicated documentation page <a href="../forms/search-input/#props">here</a>
    h4 Views 
    section.chi-table.chi-table__options.-bordered.-my--3 
      div(style='overflow-x:auto;')
        table.-text(cellpadding='0' cellspacing='0')
          thead 
            tr 
              th
                div Property
              th
                div Description
              th
                div Type
              th
                div Default
          tbody
            tr
              td
                div
                  code views
              td
                div To define views in the toolbar.
              td
                div
                  code DataTableView[]
              td
                div
                  | []
            tr
              td
                div
                  code defaultView
              td
                div To define the default view in the toolbar.
              td
                div
                  code string
              td
                div
                  | undefined
    h4 Filters
    section.chi-table.chi-table__options.-bordered.-my--3
      div(style='overflow-x:auto;')
        table.-text(cellpadding='0' cellspacing='0')
          thead
            tr
              th
                div Property
              th
                div Description
              th
                div Type
              th
                div Default
          tbody
            tr
              td
                div
                  code filtersData
              td
                div To define filters in the toolbar.
              td
                div
                  code DataTableFilters[]
              td
                div
                  | undefined
            tr
              td
                code customItems
              td
                | To define custom items in the toolbar.
              td
                code DataTableCustomItem[]
              td
                | undefined
    h4 Column customization
    section.chi-table.chi-table__options.-bordered.-my--3
      div(style='overflow-x:auto;')
        table.-text(cellpadding='0' cellspacing='0')
          thead
            tr
              th
                div Property
              th
                div Description
              th
                div Type
              th
                div Default
          tbody
            tr
              td
                div
                  code columnsData
              td
                div To define columns for customization.
              td
                div
                  code DataTableColumns[]
              td
                div
                  | undefined
    h3 Interfaces and types
    section.chi-table.chi-table__options.-bordered.-my--3
      div(style='overflow-x:auto;')
        table.-types(cellpadding='0' cellspacing='0')
          thead
            tr
              th
                div Name
              th
                div Interface
          tbody
            tr
              td
                div
                  code DataTableFilter
              td.-p--0
                pre.-mb--0.
                  {
                    name: <code>string</code>;
                    label: <code>string</code>;
                    type: <code>'select' | 'input' | 'checkbox' | 'textarea'</code>;
                    id: <code>string</code>;
                    options?: [
                      {
                        value: <code>string</code>;
                        label: <code>string</code>;
                        selected: <code>true</code>;
                      }
                    ];
                    value?: <code>string</code>;
                    checked?: <code>boolean</code>;
                    defaultValue?: <code>string</code>;
                    placeholder: <code>string</code>;
                    advanced?:<code>true</code>;
                  }
            tr
              td
                div
                  code DataTableColumn
              td.-p--0
                pre.-mb--0.
                  {
                    name: <code>string</code>;
                    label: <code>string</code>;
                    selected: <code>boolean</code>;
                    locked: <code>true</code>;
                  }
            tr
              td
                div
                  code DataTableView
              td.-p--0
                pre.-mb--0.
                  {
                    id: <code>string</code>;
                    label: <code>string</code>;
                    searchString?: <code>string</code>;
                    columns?: <code>DataTableColumn[]</code>;
                    filters?: <code>DataTableFilter[]</code>;
                  }
    h3 Events
    section.chi-table.chi-table__options.-bordered.-my--3
      div(style='overflow-x:auto;')
        table.-text(cellpadding='0' cellspacing='0')
          thead
            tr
              th
                div Event
              th
                div Description
              th
                div Type
          tbody
            tr
              td
                div
                  code chiToolbarFiltersChange
              td
                div To user has changed the filter options of the data table
              td
                div
                  code DataTableFilters[]
            tr
              td
                div
                  code chiToolbarSearch
              td
                div The user has made a search in the data table
              td
                div
                  code string
            tr
              td
                div
                  code chiToolbarColumnsChange
              td
                div The user has changed the configuration of the columns
              td
                div
                  code DataTableColumns[]
            tr
              td
                div
                  code chiToolbarViewsChange
              td
                div The user has selected a view
              td
                div
                  code DataTableView
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({})
export default class Properties extends Vue {}
</script>
