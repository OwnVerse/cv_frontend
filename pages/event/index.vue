<template>
    <div>
        <cli-title class="title" page-index="4"></cli-title>
        <div class="menu">
            <cli-menu></cli-menu>
        </div>
        <div class="center">
            <elder-event-list ref="elderEventList"></elder-event-list>
            <div style="margin-top: 30px"></div>
            <intrusion-event-list ref="intrusionEventList"></intrusion-event-list>
        </div>
    </div>

</template>

<script>
    import CliTitle from "../../components/base/cliTitle";
    import CliMenu from "../../components/base/cliMenu";
    import elderEventList from "../../components/event/elderEventList";
    import intrusionEventList from "../../components/event/intrusionEventList";
    import GET from "../../api";

    export default {
        name: "index",
        components: {CliTitle, CliMenu, elderEventList, intrusionEventList},
        data() {
            return {

            }
        },
        mounted() {
            this.getEvents();
        },
        methods: {
            getEvents() {
                let data = {};
                GET.eventList(data).then(res => {
                    console.log(res);
                    let len = res.length;
                    console.log(len);
                    let elderEventData = [];
                    let intrusionEventData = [];
                    for (let i = 0; i < len; i++) {
                        if(res[i].event_type===0 || res[i].event_type===1){
                            let tmp={
                                ID: res[i].id,
                                date: res[i].event_date,
                                name: res[i].oldperson_id.username,
                                address: res[i].event_location,
                                description: res[i].event_desc,
                                tag: res[i].event_type === 0 ? '微笑' : '交互',
                            };
                            elderEventData.push(tmp);
                        }else{
                            let tmp={
                                ID: res[i].id,
                                date: res[i].event_date,
                                address: res[i].event_location,
                                description: res[i].event_desc,
                                tag: res[i].event_type === 2 ? '陌生人来访' : (res[i].event_type === 3 ? '摔倒' : '禁止区域入侵'),
                            };
                            intrusionEventData.push(tmp);
                        }
                    }
                    this.$refs.elderEventList.setData(elderEventData);
                    this.$refs.intrusionEventList.setData(intrusionEventData);
                })
            },
        }
    }
</script>

<style scoped>
    @import "../../assets/css/page.css";
</style>
