<template>
    <el-aside :width="$store.state.isCollapse ? '180px' : '64px'">
        <el-menu class="el-menu-vertical-demo" background-color="#545c64" text-color="#fff"
            :collapse="!$store.state.isCollapse" :collapse-transition="false">
            <el-menu-item :index="item.path" v-for="item in noChildren()" :key="item.path" @click="clickMenu(item)">
                <component class="icons" :is="item.icon"></component>
                <span>{{ item.label }}</span>
            </el-menu-item>
            <el-sub-menu :index="item.path" v-for="item in hasChildren()" :key=item.path>
                <template #title>
                    <component class="icons" :is="item.icon"></component>
                    <span>{{ item.label }}</span>
                </template>
                <el-menu-item-group>
                    <el-menu-item :index="subItem.path" v-for="(subItem, subIndex) in item.children" :key="subIndex"
                        @click="clickMenu(subItem)">
                        <component class="icons" :is="subItem.icon"></component>
                        <span>{{ subItem.label }}</span>
                    </el-menu-item>
                </el-menu-item-group>
            </el-sub-menu>
        </el-menu>
    </el-aside>
</template>

<script>
import { useRouter } from 'vue-router'
export default {
    setup() {
        const list = [
            {
                path: "/",
                name: "home",
                label: "首页",
                icon: "house",
                url: "Home/Home",
            },
            {
                path: "/mall",
                name: "mall",
                label: "货物管理",
                icon: "document",
                url: "MallManage/MallManage",
            },
            {
                path: "/user",
                name: "user",
                label: "用户管理",
                icon: "user",
                url: "UserManage/UserManage",
            },
            {
                label: "其他",
                icon: "location",
                path: "/other",
                children: [
                    {
                        path: "/page1",
                        name: "page1",
                        label: "页面1",
                        icon: "setting",
                        url: "Other/PageOne",
                    },
                    {
                        path: "/page2",
                        name: "page2",
                        label: "页面2",
                        icon: "setting",
                        url: "Other/PageTwo",
                    },
                ],
            },
        ];
        const router = useRouter();
        const noChildren = () => {
            return list.filter((item) => !item.children);
        };
        const hasChildren = () => {
            return list.filter((item) => item.children);
        };
        const clickMenu = (item) => {
            router.push({
                name:item.name,
            });
        };
        return {
            noChildren,
            hasChildren,
            clickMenu,
        };
    },
}
</script>

<style lang="less" scoped>
.icons {
    width: 18px;
    height: 18px;
}

.el-menu {
    height: 100%;
    border-right: none;
}
</style>