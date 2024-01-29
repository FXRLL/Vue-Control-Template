<template>
    <div class="common-layout">
        <el-container class="lay-container">
            <CommonAside></CommonAside>
            <el-container class="r-container">
                <CommonHeader></CommonHeader>
                <el-main>
                    <router-view />
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
import { defineComponent } from 'vue';
import CommonHeader from '../components/CommonHeader.vue'
import CommonAside from '../components/CommonAside.vue'
export default defineComponent({
    components: {
        CommonHeader,
        CommonAside,
    },
});
</script>

<style lang="less" scoped>
.r-container {
    flex-wrap: wrap;
    flex-direction: column;
}

.common-layout {
    height: 100%;
}

.common-layout .el-container {
    height: 100%;
}
</style>