<template>
  <div>
    <head-nav/>
    <p/>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="3">
          <b-list-group>
            <b-list-group-item>Create New Agent</b-list-group-item>
            <b-list-group-item>View Agents Diagram</b-list-group-item>
            <b-list-group-item>Hide Disabled Agents</b-list-group-item>
          </b-list-group>
          <p/>
          <b-form-group
            id="fieldset1"
            v-model="perPage"
            :description="'Show ' + perPage + ' agents in every page.'"
            label-for="input1"
          >
            <b-form-select 
              :options="pageOptions" 
              v-model="perPage"/>
          </b-form-group>
          <p/>
          <b-pagination
            :total-rows="totalRows"
            :per-page="perPage"
            v-model="currentPage"
            align="center"
            class="my-0"
            size="sm"
            hide-ellipsis
          />
        </b-col>
        <b-col sm="9">
          <b-pagination
            :total-rows="totalRows"
            :per-page="perPage"
            v-model="currentPage"
            align="center"
            class="my-0"
            size="md"
            limit="15"
          />
          <p/>
          <div 
            id="listgroup-ex" 
            style="position:relative;overflow-y:auto;height:90">
            <b-table 
              :current-page="currentPage"
              :fields="fields"
              :items="items"
              :per-page="perPage"
              striped
              hover
            >
              <template 
                slot="index"
                slot-scope="data">
                {{data.index + 1}}
              </template>
              <template
                slot="management"
                slot-scope="data">
                <b-dropdown size="sm" id="ddown1" text="M" class="m-md-2">
                  <b-dropdown-item>Run</b-dropdown-item>
                  <b-dropdown-item>Dry Run</b-dropdown-item>
                  <!--<b-dropdown-item>Show</b-dropdown-item>-->
                  <b-dropdown-divider></b-dropdown-divider>
                  <b-dropdown-item>Edit</b-dropdown-item>
                  <b-dropdown-item>Clone</b-dropdown-item>
                  <b-dropdown-item>Disable</b-dropdown-item>
                  <b-dropdown-divider></b-dropdown-divider>
                  <!--<b-dropdown-item>Remove Events</b-dropdown-item>-->
                  <b-dropdown-item>Delete</b-dropdown-item>
                </b-dropdown>
              </template>
            </b-table>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
  import HeadNav from '~/components/Nav.vue'

  const items = [
    {name:"xxx",scenarios:0,type:1,schedute:60,lastRun:0,lastEvent:4,eventsCreated:100},
    {name:"xsxx xxxxxxxxxxxxxxxx",type:1,schedute:60,lastRun:0,lastEvent:4,eventsCreated:100,scenarios:2},
    {name:"xxx",scenarios:0,type:1,schedute:60,lastRun:0,lastEvent:4,eventsCreated:100}
  ]

  export default {
    components: {
      HeadNav
    },
    data() {
      return {
        items: items,
        fields: [
          'index',
          { key: 'name', label: 'Agent Name' },
          'scenarios',
          'lastRun',
          'lastEvent',
          'eventsCreated',
          'management'
        ],
        perPage: 5,
        currentPage: 1,
        totalRows: items.length,
        pageOptions: [5, 10, 15, 20, 25, 30]
      }
    }
  }
</script>
