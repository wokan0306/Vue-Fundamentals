<template>
  <div>
    <el-container style="height: 700px; border: 1px solid #eee">
      <el-header style="font-size: 40px; background-color: rgb(238, 241, 246)"
        >tlias Intelligent Learning Assistant System</el-header
      >
      <el-container>
        <el-aside width="280px" style="background-color: rgb(238, 241, 246); border: 1px solid #eee">
          <el-menu :default-openeds="['1', '3']">
            <el-submenu index="1">
              <template slot="title"
                ><i class="el-icon-message"></i>System Information Management</template>
              <el-menu-item-group>
                <el-menu-item index="1-1"><router-link to="/dept">Department Management</router-link></el-menu-item>
                <el-menu-item index="1-2"><router-link to="/emp">Employee Management</router-link></el-menu-item>
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
        </el-aside>

        <el-main>
          <el-form :inline="true" :model="searchForm" class="demo-form-inline">
            <el-form-item label="Name">
              <el-input v-model="searchForm.name" placeholder="Name"></el-input>
            </el-form-item>
            <el-form-item label="Gender">
              <el-select v-model="searchForm.gender" placeholder="Gender">
                <el-option label="Male" value="1"></el-option>
                <el-option label="Female" value="2"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="Entry Date">
              <!-- Date Picker -->
              <el-date-picker
                v-model="searchForm.entryDate"
                type="daterange"
                range-separator="To"
                start-placeholder="Start date"
                end-placeholder="End date"
              >
              </el-date-picker>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">Query</el-button>
            </el-form-item>
          </el-form>
          <el-table :data="tableData" border>
            <el-table-column
              prop="name"
              label="Name"
              width="180"
            ></el-table-column>
            <el-table-column
              label="Image"
              width="180"
            >
            <template slot-scope="scope">
                    <img :src="scope.row.image" width="100px">
            </template>
            </el-table-column>
            <el-table-column
              label="Gender"
              width="140"
            >
            <template slot-scope="scope">
                {{scope.row.gender == 1? 'Male': 'Female'}}
            </template>
            </el-table-column>
            <el-table-column
              prop="job"
              label="Position"
              width="140"
            ></el-table-column>
            <el-table-column
              prop="entrydate"
              label="Entry Date"
              width="180"
            ></el-table-column>
            <el-table-column
              prop="updatetime"
              label="Last Update Time"
              width="230"
            ></el-table-column>
            <el-table-column label="Action">
              <el-button type="primary" size="mini">Edit</el-button>
              <el-button type="danger" size="mini">Delete</el-button>
            </el-table-column>
          </el-table>
          <el-pagination
              background
              layout="sizes, prev, pager, next, jumper, total"
              @size-change="handleSizeChange"
              @current-change="handleCurrentChange"
              :total="1000"
            >
            </el-pagination>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      tableData: [],
      searchForm: {
        user: "",
        gender: "",
        entrydate: [],
      },
    };
  },
  methods: {
    onSubmit() {
      alert("submit!");
    },
    handleSizeChange(val) {
      alert("Each page record number changes " + val);
    },
    handleCurrentChange(val) {
      alert("Page number changes " + val);
    }
  },
  mounted() {
    axios.get("http://api.doc.jiyou-tech.com/mock/14635/user/getById").then((result)=> {
        this.tableData = result.data.data;
    })
  },
};
</script>

<style>
</style>