<template>
    <div>
        <el-container style="height: 700px; border: 1px solid #eee">
            <el-header style="font-size:40px; background-color: rgb(238, 241, 246)">tlias Intelligent Learning Assistant System</el-header>
            <el-container>
                <el-aside width="280px" style="border: 1px solid #eee">
                    <el-menu :default-openeds="['1', '3']">
                        <el-submenu index="1">
                            <template slot="title"><i class="el-icon-message"></i>System Information Management</template>
                            <el-menu-item index="1-1">
                                <router-link to="/dept">Department Management</router-link>
                            </el-menu-item>
                            <el-menu-item index="1-2">
                                <router-link to="/emp">Employee Management</router-link>
                            </el-menu-item>
                        </el-submenu>
                    </el-menu>
                </el-aside>

                <el-main>
                    <!-- Table -->
                    <el-table :data="tableData" border>
                        <el-table-column prop="name" label="Name" width="250"></el-table-column>
                        <el-table-column prop="updatetime" label="Last Operation Time" width="250"></el-table-column>
                        <el-table-column label="Action">
                            <el-button type="primary" size="mini">Edit</el-button>
                            <el-button type="danger" size="mini">Delete</el-button>
                        </el-table-column>
                    </el-table>
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tableData: [{
                id: 1,
                name: "Department of Student Affairs",
                updatetime: "2010-01-01 12:00:00"
            }, {
                id: 2,
                name: "Department of Academic Research",
                updatetime: "2010-01-01 12:00:00"
            }, {
                id: 3,
                name: "Department of Employment",
                updatetime: "2010-01-01 12:00:00"
            }, {
                id: 4,
                name: "Human Resources Department",
                updatetime: "2010-01-01 12:00:00"
            }, {
                id: 5,
                name: "Administrative Department",
                updatetime: "2010-01-01 12:00:00"
            }]
        }
    },
    methods: {

    }
}
</script>

<style>

</style>