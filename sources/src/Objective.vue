<template>
    <div>
        <el-collapse v-for="item in data" :key="item._id">
            <el-collapse-item>
                <template slot="title" style="height: 60px">
                    <img 
                            src="../../public/img/bullseye.png"
                            style="width: 25px; height: 25px; border-radius: 15px; margin-left: 10px"/>
                    <span style="margin-left: 20px; width: 60%; font-size: 14.5px">{{item.name.toUpperCase()}}</span>
                    <el-progress :percentage="item.progress" style="width: 20%"></el-progress>
                    <span style="width: 8%">
                        KR:
                        <span style="border: 1px solid black; padding: 5px 9px; border-radius: 50%; margin-left: 5px">
                            {{item.key_result.length}}
                        </span>
                    </span>
                    <span style="width: 3%">
                        <i 
                                class="el-icon-edit" 
                                style="font-size: 20px; color: #409EFF; margin: auto" 
                                @click="$router.push({name: 'objective', params: {id: item._id}})">
                        </i>
                    </span>
                </template>
                <el-table
                        style="margin: -45px auto auto; width: 90%"
                        v-if="item.key_result.length"
                        :data="item.key_result">
                    <el-table-column>
                        <template slot-scope="scope">
                            <i class="el-icon-star-on"></i>
                            <span style="margin-left: 10px; width: 60%">{{scope.row.name}}</span>
                            <el-progress :percentage="scope.row.progress" style="width: 15%; float: right"></el-progress>
                        </template>
                    </el-table-column>
                </el-table>
            </el-collapse-item>
        </el-collapse>
    </div>
</template>

<script>
export default {
    data() {
        return{}
    },
    props: {
        data: {
            type: Array,
            required: true
        }
    }
}
</script>

<style lang="scss" scoped>
.el-progress-bar {
    margin-right: 100px
}
.el-icon-star-on {
    font-size: 20px;
    color: #409EFF
}
</style>