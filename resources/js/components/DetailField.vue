<template>
  <r64-panel-item
    :field="field"
    :hide-label="hideLabelInDetail"
    :label-classes="panelLabelClasses"
    :field-classes="panelFieldClasses"
  >
    <r64-excerpt
      slot="value"
      :content="field.value"
      :excerpt-classes="excerptClasses"
      :show-label="showContentLabel"
      :hide-label="hideContentLabel"
    >
      <template slot="content">
        <RowHeading
          v-if="!field.hideHeading"
          :fields="field.fields"
        />
        <div
          v-for="row in values"
          :key="row.row_id"
          class="flex border-40 border"
        >
          <p
            v-for="f in field.fields"
            :key="`${row.row_id}${f.attribute}`"
              :class="f.fieldClasses"
          >{{ row[f.attribute] }}</p>
        </div>
      </template>
    </r64-excerpt>
  </r64-panel-item>
</template>

<script>
import R64Field from './R64Field';
import RowHeading from './RowHeading';
import RowField from './RowField';

export default {
  mixins: [RowField, R64Field],

  components: { RowHeading },

  props: ['resource', 'resourceName', 'resourceId', 'field']
};
</script>
