<script>
import { defineComponent } from 'vue';
import CommonHeader from '../components/CommonHeader.vue'
export default defineComponent({
    components: {
        CommonHeader,
    },
});

</script>
<template>
    <div class="common-layout">
        <el-container class="lay-container">
            Aside
            <el-container class="r-container">
                <CommonHeader></CommonHeader>
                <el-main>Main
                    <router-view />
                </el-main>
            </el-container>
        </el-container>
    </div>
</template>

<style>
.r-container{
    flex-wrap:wrap;
}
</style>