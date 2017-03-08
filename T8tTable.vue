<template>

    <el-table
        :data="dataSource"
        :height="height"
        :stripe="stripe"
        :border="border"
        :fit="fit"
        :show-header="showHeader"
        :highlight-current-row="highlightCurrentRow"
        :current-row-key="currentRowKey"
        :row-class-name="rowClassName"
        :row-style="rowStyle"
        :row-key="rowKey"
        :empty-text="emptyText"
        :default-expand-all="defaultExpandAll"
        :expand-row-keys="expandRowKeys"
        :default-sort="defaultSort"
        v-on:select="onSelect"
        v-on:select-all="onSelectAll"
        v-on:row-click="onRowClick"
        v-on:selection-change="onSeletionChange"
        v-on:cell-mouse-enter="onCellMouseEnter"
        v-on:cell-mouse-leave="onCellMouseLeave"
        v-on:cell-click="onCellClick"
        v-on:cell-dblclick="onCellDbClick"
        v-on:row-contextmenu="onRowContextmenu"
        v-on:row-dblclick="onRowDbClick"
        v-on:header-click="onHeaderClick"
        v-on:sort-change="onSortChange"
        v-on:filter-change="onFilterChange"
        v-on:current-change="onCurrentChange"
        v-on:header-dragend="onHeaderDragend"
        v-on:expand="onExpand"
    >
        <el-table-column
            v-for="item in columns"
            :type="item.type"
            :column-key="item.columnKey"
            :min-width="item.minWidth"
            :fixed="item.fixed"
            :render-header="item.renderHeader"
            :sortable="item.sortable"
            :sort-method="item.sortMethod"
            :resizable="item.resizable"
            :formatter="item.formatter"
            :show-overflow-tooltip="item.showOverFlowTooltip"
            :align="item.align"
            :header-align="item.headerAlign"
            :class-name="item.className"
            :selectable="item.selectable"
            :reserve-selection="item.reserveSelection"
            :filters="item.filters"
            :filter-multiple="item.filterMultiple"
            :filter-method="item.filterMethod"
            :filtered-value="item.filteredValue"
            :prop="item.prop"
            :label="item.label"
            :width="item.width">
        </el-table-column>
    </el-table>

</template>

<script>

export default {
    name: 't8t-table',
    props: {
        columns: Array,
        dataSource: Array,
        height: Number,
        stripe: Boolean,
        border: {
            type: Boolean,
            default: true
        },
        fit: {
            type: Boolean,
            default: true
        },
        "showHeader": {
            type: Boolean,
            default: true
        },
        "highlightCurrentRow": {
            type: Boolean,
            default: false
        },
        "currentRowKey": [String, Number],
        "rowClassName": [String, Function],
        "rowStyle": [Object, Function],
        "rowKey": [Function, String],
        "emptyText": {
            type: String,
            default: "暂无数据"
        },
        "defaultExpandAll": {
            type: Boolean,
            default: false
        },
        "expandRowKeys": Array,
        "defaultSort": Object
    },
    data() {
        return {
            
        }
    },
    methods: {
        onSelect(selection, row) {
            this.$emit('select', selection, row)
        },
        onSelectAll(selection) {
            this.$emit('selectAll', selection)
        },
        onSeletionChange(selection) {
            this.$emit('selectionChange', selection)
        },
        onCellMouseEnter(row, column, cell, event) {
            this.$emit('cellMouseEnter', row, column, cell, event)
        },
        onCellMouseLeave(row, column, cell, event) {
            this.$emit('cellMouseLeave', row, column, cell, event)
        },
        onRowClick(row, event, column) {
            this.$emit('rowClick', row, event, column)
        },
        onCellClick(ow, column, cell, event) {
            this.$emit('CellClick', row, event, column)
        },
        onCellDbClick(row, column, cell, event) {
            this.$emit('cellDbClick', row, column, cell, event)
        },
        onRowContextmenu(row, event) {
            this.$emit('rowContextmenu', row, event)
        },
        onRowDbClick(row, event) {
            this.$emit('rowDbClick', row, event)
        },
        onHeaderClick(column, event) {
            this.$emit('headerClick', column, event)
        },
        onSortChange(event) {
            this.$emit('sortChange', event)
        },
        onFilterChange(filters) {
            this.$emit('filterChange', filters)
        },
        onCurrentChange(currentRow, oldCurrentRow) {
            this.$emit('currentChange', currentRow, oldCurrentRow)
        },
        onHeaderDragend(newWidth, oldWidth, column, event) {
            this.$emit('headerDragend', newWidth, oldWidth, column, event)
        },
        onExpand(row, expanded) {
            this.$emit('expand', row, expanded)
        }
    }

}    
</script>