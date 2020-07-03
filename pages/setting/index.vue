<template>
    <div>
        <cli-title class="title"></cli-title>
        <div class="menu">
            <cli-menu></cli-menu>
        </div>
        <div class="center">
            <div>
                <div style="margin-left: 100px; width: 100px; display: inline-block;">
                    <img :src="picPath" alt="">
                </div>
                <div style="margin-left: 100px; width: 400px; display: inline-block;">
                    <el-row>
                        <span class="text">管理员账号</span>
                    </el-row>
                    <div style="margin: 8px 0;"></div>
                    <el-row>
                        <el-input
                                type="text"
                                placeholder="管理员账号"
                                v-model="title"
                                maxlength="10"
                                show-word-limit
                                disabled="true"
                        >
                        </el-input>
                    </el-row>
                    <div style="margin: 15px 0;"></div>
                    <el-row>
                        <span class="text">管理员昵称</span>
                    </el-row>
                    <div style="margin: 8px 0;"></div>
                    <el-row>
                        <el-input
                                type="textarea"
                                placeholder="管理员昵称"
                                v-model="description"
                                maxlength="10"
                                show-word-limit
                        >
                        </el-input>
                    </el-row>
                </div>
            </div>
            <div style="margin-top: 100px; margin-left: 100px">
                <el-tabs :tab-position="tabPosition" style="height: 300px;">
                    <el-tab-pane label="账号">
                        <el-row>原密码:
                            <el-input
                                    type = "password"
                                    v-model = "message"
                                    maxlength = "12">
                            </el-input>
                        </el-row>

                        <el-row>新密码:
                            <el-input
                                    type = "password"
                                    v-model = "message"
                                    maxlength = "12">
                            </el-input>
                        </el-row>

                        <el-row>确认新密码:
                            <el-input
                                    type = "password"
                                    v-model = "message"
                                    maxlength = "12">
                            </el-input>
                        </el-row>

                        <button v-on:click=""  style = "font-size:15px;">更新密码</button>

                    </el-tab-pane>
                    <el-tab-pane label="通知">
                         <el-row>手机号:
                            <el-input
                                    type = "textarea"
                                    v-model = "message"
                                    maxlength = "12">
                            </el-input>
                        </el-row>

                        <el-row>邮箱:
                            <el-input
                                    type = "textarea"
                                    v-model = "message"
                                    maxlength = "12">
                            </el-input>
                        </el-row>
                        <el-row>是否接收通知：
                            <input
                                    type="range"
                                    min="0"
                                    max="100"
                                    value="0"
                            />
                        </el-row>

                        <button v-on:click=""  style = "font-size:15px;">更新通知</button>

                    </el-tab-pane>
                    <el-tab-pane label="设置">

                    </el-tab-pane>
                </el-tabs>
            </div>
        </div>
    </div>
</template>

<script>
    import CliTitle from "../../components/base/cliTitle";
    import CliMenu from "../../components/base/cliMenu";
    import pic from "../../assets/image/people.png";

    export default {
        name: "index",
        components: {CliTitle, CliMenu},
        data() {
            return {
                picPath: pic,
                tabPosition: 'left'
            }
        },
        methods: {}
    }
</script>

<style scoped>
    @import "../../assets/css/page.css";
</style>
