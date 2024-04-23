<template>
  <div>
    <el-row>
      <el-button>Default</el-button>
      <el-button type="primary">Primary</el-button>
      <el-button type="success">Success</el-button>
      <el-button type="info">Info</el-button>
      <el-button type="warning">Warning</el-button>
      <el-button type="danger">Danger</el-button>
    </el-row>
    <hr />
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="Date" width="180"> </el-table-column>
      <el-table-column prop="name" label="Name" width="180"> </el-table-column>
      <el-table-column prop="address" label="Address"> </el-table-column>
    </el-table>
    <hr />
    <el-pagination
      background
      layout="sizes, prev, pager, next, jumper, total"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :total="1000"
    >
    </el-pagination>

    <!-- Table -->
    <el-button type="text" @click="dialogTableVisible = true"
      >open a Table nested Dialog</el-button
    >

    <el-dialog title="Shipping address" :visible.sync="dialogTableVisible">
      <el-table :data="gridData">
        <el-table-column
          property="date"
          label="Date"
          width="150"
        ></el-table-column>
        <el-table-column
          property="name"
          label="Name"
          width="200"
        ></el-table-column>
        <el-table-column property="address" label="Address"></el-table-column>
      </el-table>
    </el-dialog>

    <hr />

    <!-- Dialog - Form  -->
    <el-button type="text" @click="dialogFormVisible = true"
      >Open Embedded Form Dialog</el-button
    >
    <el-dialog title="Form" :visible.sync="dialogFormVisible">
      <el-form ref="form" :model="form" label-width="120px">
        <el-form-item label="Activity name">
          <el-input v-model="form.name"></el-input>
        </el-form-item>
        <el-form-item label="Activity zone">
          <el-select
            v-model="form.region"
            placeholder="please select your zone"
          >
            <el-option label="Zone one" value="shanghai"></el-option>
            <el-option label="Zone two" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="Activity time">
          <el-col :span="11">
            <el-date-picker
              type="date"
              placeholder="Pick a date"
              v-model="form.date1"
              style="width: 100%"
            ></el-date-picker>
          </el-col>
          <el-col class="line" :span="2">-</el-col>
          <el-col :span="11">
            <el-time-picker
              placeholder="Pick a time"
              v-model="form.date2"
              style="width: 100%"
            ></el-time-picker>
          </el-col>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">Submit</el-button>
          <el-button>Cancel</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [
        {
          date: "2016-05-03",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
        },
        {
          date: "2016-05-02",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
        },
        {
          date: "2016-05-04",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
        },
        {
          date: "2016-05-01",
          name: "Tom",
          address: "No. 189, Grove St, Los Angeles",
        },
      ],
      gridData: [
        {
          date: "2016-05-02",
          name: "John Smith",
          address: "No.1518,  Jinshajiang Road, Putuo District",
        },
        {
          date: "2016-05-04",
          name: "John Smith",
          address: "No.1518,  Jinshajiang Road, Putuo District",
        },
        {
          date: "2016-05-01",
          name: "John Smith",
          address: "No.1518,  Jinshajiang Road, Putuo District",
        },
        {
          date: "2016-05-03",
          name: "John Smith",
          address: "No.1518,  Jinshajiang Road, Putuo District",
        },
      ],
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
      },
      formLabelWidth: "120px",
    };
  },
  methods: {
    handleSizeChange(val) {
      alert("Each page record number changes " + val);
    },
    handleCurrentChange(val) {
      alert("Page number changes " + val);
    },
    onSubmit() {
      alert(JSON.stringify(this.form));
    },
  },
};
</script>

<style>
</style>