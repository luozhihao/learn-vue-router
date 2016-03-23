<template>
    <div class="panel panel-default">
        <div class="panel-heading">
            <h3 class="panel-title">Panel title</h3>
        </div>
        <div class="panel-body">
            <div>
                <alert-view :msg="msgTxt"></alert-view>
                <!-- Nav tabs -->
                <ul class="nav nav-tabs" role="tablist">
                    <li role="presentation" class="active">
                        <a href="#home" aria-controls="home" role="tab" data-toggle="tab">图表</a>
                    </li>
                    <li role="presentation">
                        <a href="#profile" aria-controls="profile" role="tab" data-toggle="tab">表格</a>
                    </li>
                    <li role="presentation">
                        <a href="#messages" aria-controls="messages" role="tab" data-toggle="tab">父子组件通信</a>
                    </li>
                    <li role="presentation">
                        <a href="#settings" aria-controls="settings" role="tab" data-toggle="tab">动画过度</a>
                    </li>
                </ul>

                <!-- Tab panes -->
                <div class="tab-content">
                    <div role="tabpanel" class="tab-pane active" id="home">
                        <div id="container">
                            
                        </div>
                    </div>
                    <div role="tabpanel" class="tab-pane" id="profile">
                        <table style="width: 100%" id="foo_table" class="table table-hover">
                            <thead>
                                <tr>
                                    <th width="10%">序号</th>
                                    <th width="80%">内容</th>
                                    <th width="10%">时间</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>01</td>
                                    <td>Vue 实例的原始数据 $data 能直接用 JSON.stringify() 序列化。</td>
                                    <td>2016-03-14</td>
                                </tr>
                                <tr>
                                    <td>02</td>
                                    <td>Vue 实例的原始数据 $data 能直接用 JSON.stringify() 序列化。</td>
                                    <td>2016-03-14</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    <div role="tabpanel" class="tab-pane" id="messages">
                        <br>
                        <button type="btn" class="btn btn-default" @click="changeMsg">改变Alert模块内容</button>
                    </div>
                    <div role="tabpanel" class="tab-pane" id="settings">
                        <div class="ani-btn col-sm-4 text-center">
                            <button type="button" class="btn btn-primary" @click="aniFn">动画按钮</button>
                        </div>
                        <div class="col-sm-8">
                            <div class="ani-box col-sm-4 col-sm-offset-4 text-center" v-show="show" transition="bounce">
                                动画对象
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
var bt = require('bootstrap'),
    Highcharts = require('highcharts'),
    dt = require('datatables.net');

export default {
    data () {
        return {
            msgTxt: '这是一条初始警告消息',
            show: true
        }
    },
    methods: {
        changeMsg () {
            this.msgTxt = '警告内容以及改变~'
        },
        aniFn () {
            this.show ? this.show = false : this.show = true
        }
    },
    ready () {
        var chart = new Highcharts.Chart({
            chart: {
                renderTo: 'container',
            },
            title: {
                text: 'Monthly Average Temperature',
                x: -20 //center
            },
            subtitle: {
                text: 'Source: WorldClimate.com',
                x: -20
            },
            xAxis: {
                categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun','Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
            },
            yAxis: {
                title: {
                    text: 'Temperature (°C)'
                },
                plotLines: [{
                    value: 0,
                    width: 1,
                    color: '#808080'
                }]
            },
            tooltip: {
                valueSuffix: '°C'
            },
            legend: {
                layout: 'vertical',
                align: 'right',
                verticalAlign: 'middle',
                borderWidth: 0
            },
            series: [{
                name: 'Tokyo',
                data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
            }, {
                name: 'New York',
                data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
            }, {
                name: 'Berlin',
                data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
            }, {
                name: 'London',
                data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
            }]
        });

        $('#foo_table').DataTable()
    },
    route: {
        data (transition) {
            console.log(123)
        }
    },
    components: {
        AlertView: require('./Index.vue')
    }
}
</script>

<style scoped>
@import url('../assets/js/datatables.net-dt/css/jquery.dataTables.css');

.ani-box {
    height: 250px;
    background: #eee;
    margin-top: 50px;
    margin-bottom: 50px;
    line-height: 250px;
}

.ani-btn {
    height: 350px;
    line-height: 350px;
}

.bounce-enter {
  animation: bounce-in .5s;
}

.bounce-leave {
  animation: bounce-out .5s;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes bounce-out {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(0);
  }
}
</style>