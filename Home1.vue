<template>
    <div class="maincontainer">
        <div class="leftcontainer" ref="leftcontainer">
            <div style="width: 220px;background-color: black;color: black;top: 0px; left: 0px; z-index: -100;">
                <img src="../../public/favicon.ico" style="width: 20;position: absolute;margin-top: 10px;margin-left: 10px;">
                <span v-show="!isCollesped" slot="title" style="position: absolute;margin-top: 10px;margin-left: 50px;font-size: larger;color: black;">Manage System</span>
            </div>
            <div style="position: absolute;top: 50px;left: 0px;width: 220px;">
                <el-menu
                :collapse="isCollesped">
                    <el-menu-item index="1">
                        <el-icon><user /></el-icon>
                        <span slot="title" style="position: absolute;left: 50px;">首页</span>
                    </el-menu-item>
                    <el-sub-menu index="2">
                        <template #title>
                            <el-icon><user /></el-icon>
                            <span slot="title">人员管理</span>
                        </template>
                        <el-menu-item index="2-1">
                            <el-icon><user /></el-icon>
                            <span>管理层人员</span>
                        </el-menu-item>
                        <el-sub-menu index="2-2">
                            <template #title>
                                <el-icon><user /></el-icon>
                                <span>科研人员</span>
                            </template>
                            <el-menu-item index="2-2-1">
                                <el-icon><user /></el-icon>
                                <span>硬件人员</span>
                            </el-menu-item> 
                            <el-menu-item index="2-2-2">
                                <el-icon><user /></el-icon>
                                <span>软件人员</span>
                            </el-menu-item>
                        </el-sub-menu>
                    </el-sub-menu>
                </el-menu>
            </div>
        </div>
        <div class="rightcontainer" ref="rightcontainer">
            <div class="righttopcontainer" ref="righttopcontainer">
                <el-button type="primary" @click="change" style="margin-top: 10px;background-color: white;border: none;">
                    <el-icon :size="20" color="black"><Fold /></el-icon>
                </el-button>
                <el-menu style="position: absolute;top: -6px;right: 0px;">
                    <el-sub-menu index="1">
                        <template #title>
                            <el-avatar src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"/>
                            <span>Login</span>
                        </template>
                        <el-menu-item index="1-1">
                            <span>个人中心</span>
                        </el-menu-item>
                        <el-menu-item index="1-2">
                            <span>退出登录</span>
                        </el-menu-item>
                    </el-sub-menu>
                </el-menu>
            </div>
            <div class="rightbottomcontainer" ref="rightbottomcontainer">
                <RouterView></RouterView>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            //
            isCollesped:false
        }
    },
    methods: {
        change() {
            this.isCollesped = !this.isCollesped
            if (this.isCollesped){
                this.$refs.leftcontainer.style.width = '40px'
                this.$refs.rightcontainer.style.width = '1470px'
                this.$refs.righttopcontainer.style.width = '1470px'
                this.$refs.rightbottomcontainer.style.width = '1470px'
            }else {
                this.$refs.leftcontainer.style.width = '220px'
                this.$refs.rightcontainer.style.width = 'calc(100vw - 220px)'
                this.$refs.righttopcontainer.style.width = 'calc(100vw - 220px)'
                this.$refs.rightbottomcontainer.style.width = 'calc(100vw - 220px)'
            }
        }
    }
}
</script>

<style>
.maincontainer {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
    display: flex;
    background-color: white;
}
.leftcontainer {
    width: 220px;
    height: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
    border: none;
    margin: 0px;
    padding: 0px;
    transition:width 0.3s ease-in-out;
}
.rightcontainer {
    width: calc(100vw - 220px);
    height: 100%;
    position: absolute;
    top: 0px;
    transition: width 0.3s ease-in-out;
    right: 0px;
    background-color: rgb(144, 149, 144);
    padding: 0px;
    margin: 0px;
}
.lefttopcontainer {
    width: 220px;
    height: 50px;
    position: absolute;
    top: 0px;
    left: 0px;
    background-color: red;
}
.leftbottomcontainer {
    width: 220px;
    height: calc(100vh - 50px);
    position: absolute;
    top: 50px;
    left: 0px;
    background-color: aqua;
}
.righttopcontainer {
    width: calc(100vw - 220px);
    height: 50px;
    position: absolute;
    top: 0px;
    left: 0px;
    background-color: white;
    border-bottom: 1px solid black;
    transition: width 0.3s ease-in-out;
    z-index: 1;
    display: flex;
    
}
.rightbottomcontainer {
    width: calc(100vw - 220px);
    height: calc(100vh - 50px);
    position: absolute;
    top: 50px;
    left: 0px;
    background-color: rgb(144, 31, 31);
    transition: width 0.3s ease-in-out;
}
</style>