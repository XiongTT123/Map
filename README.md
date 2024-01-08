<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>中国各份平均受教育年限地图</title>
    <!-- 引入 ECharts -->
    <script src="https://cdn.jsdelivr.net/npm/echarts/dist/echarts.min.js"></script>
    <!-- 引入中国地图数据 -->
    <script src="https://cdn.jsdelivr.net/npm/echarts/map/js/china.js"></script>
</head>
<body>

<div id="educationMap" style="width: 800px; height: 600px; margin: auto;"></div>

<script>
    var data1 = [{'province': '北京', 'averageEducation': 9.99}, {'province': '天津', 'averageEducation': 8.99}, {'province': '河北', 'averageEducation': 7.74}, {'province': '山西', 'averageEducation': 8.02}, {'province': '内蒙古', 'averageEducation': 7.76}, {'province': '辽宁', 'averageEducation': 8.41}, {'province': '吉林', 'averageEducation': 8.24}, {'province': '黑龙江', 'averageEducation': 8.25}, {'province': '上海', 'averageEducation': 9.3}, {'province': '浙江', 'averageEducation': 7.46}, {'province': '安徽', 'averageEducation': 6.98}, {'province': '福建', 'averageEducation': 7.49}, {'province': '江西', 'averageEducation': 7.55}, {'province': '山东', 'averageEducation': 7.58}, {'province': '河南', 'averageEducation': 7.72}, {'province': '湖北', 'averageEducation': 7.77}, {'province': '湖南', 'averageEducation': 7.8}, {'province': '广东', 'averageEducation': 8.07}, {'province': '广西', 'averageEducation': 7.57}, {'province': '海南', 'averageEducation': 7.68}, {'province': '重庆', 'averageEducation': 7.28}, {'province': '四川', 'averageEducation': 7.06}, {'province': '贵州', 'averageEducation': 6.15}, {'province': '云南', 'averageEducation': 6.33}, {'province': '西藏', 'averageEducation': 3.43}, {'province': '陕西', 'averageEducation': 7.71}, 
{'province': '甘肃', 'averageEducation': 6.54}, {'province': '青海', 'averageEducation': 6.12}, {'province': '宁夏', 'averageEducation': 7.03}, {'province': '新疆', 'averageEducation': 7.73}, {'province': '江苏', 'averageEducation': 7.85}];

    var data2 = [{'province': '北京', 'averageEducation': 11.71}, {'province': '天津', 'averageEducation': 10.38}, {'province': '河北', 'averageEducation': 9.12}, {'province': '山西', 'averageEducation': 9.52}, {'province': '内蒙古', 'averageEducation': 9.22}, {'province': '辽宁', 'averageEducation': 9.67}, {'province': '吉林', 'averageEducation': 9.49}, 
{'province': '黑龙江', 'averageEducation': 9.36}, {'province': '上海', 'averageEducation': 10.73}, {'province': '浙江', 'averageEducation': 8.79}, {'province': '安徽', 'averageEducation': 8.28}, {'province': '福建', 'averageEducation': 9.02}, {'province': '江西', 'averageEducation': 8.86}, {'province': '山东', 'averageEducation': 8.97}, {'province': '河南', 'averageEducation': 8.95}, {'province': '湖北', 'averageEducation': 9.2}, {'province': '湖南', 'averageEducation': 9.16}, {'province': '广东', 'averageEducation': 9.55}, {'province': '广西', 'averageEducation': 8.76}, {'province': '海南', 'averageEducation': 9.22}, {'province': '重庆', 'averageEducation': 8.75}, {'province': '四川', 'averageEducation': 8.35}, {'province': '贵州', 'averageEducation': 7.65}, {'province': '云南', 'averageEducation': 7.76}, {'province': '西藏', 'averageEducation': 5.25}, {'province': '陕西', 'averageEducation': 9.36}, {'province': '甘肃', 'averageEducation': 8.19}, {'province': '青海', 'averageEducation': 7.85}, {'province': '宁夏', 'averageEducation': 8.82}, {'province': '新疆', 'averageEducation': 9.27}, {'province': '江苏', 'averageEducation': 9.32}];

    var data3 = [{'province': '北京', 'averageEducation': 12.21}, {'province': '天津', 'averageEducation': 10.87}, {'province': '河北', 'averageEducation': 9.35}, {'province': '山西', 'averageEducation': 10.03}, {'province': '内蒙古', 'averageEducation': 9.74}, {'province': '辽宁', 'averageEducation': 10.06}, {'province': '吉林', 'averageEducation': 9.88}, {'province': '黑龙江', 'averageEducation': 9.69}, {'province': '上海', 'averageEducation': 11.5}, {'province': '浙江', 'averageEducation': 9.51}, {'province': '安徽', 'averageEducation': 9.01}, {'province': '福建', 'averageEducation': 9.25}, {'province': '江西', 'averageEducation': 9.23}, {'province': '山东', 'averageEducation': 9.37}, {'province': '河南', 'averageEducation': 9.26}, {'province': '湖北', 'averageEducation': 9.66}, {'province': '湖南', 'averageEducation': 9.45}, {'province': '广东', 'averageEducation': 9.88}, {'province': '广西', 'averageEducation': 9.01}, {'province': '海南', 'averageEducation': 9.61}, {'province': '重庆', 'averageEducation': 9.47}, {'province': '四川', 'averageEducation': 8.95}, {'province': '贵州', 'averageEducation': 8.37}, {'province': '云南', 'averageEducation': 8.51}, {'province': '西藏', 'averageEducation': 6.62}, {'province': '陕西', 'averageEducation': 9.84}, {'province': '甘肃', 'averageEducation': 8.79}, {'province': '青海', 'averageEducation': 8.47}, {'province': '宁夏', 'averageEducation': 9.37}, {'province': '新疆', 'averageEducation': 9.43}, {'province': '江苏', 'averageEducation': 9.83}];

    var timelineData = ['2000.11', '2010.11', '2020.11'];
    var currentIndex = 0;

    function handleData(educationData, timelineDate) {
        // 初始化ECharts图表
        var educationMap = echarts.init(document.getElementById('educationMap'));

        // 获取最大和最小的受教育年限，用于颜色映射
        var maxEducation = 3;
        var minEducation = 12;

        // 构建ECharts地图的配置项
        var option = {
            baseOption: {
                timeline: {
                    axisType: 'category',
                    autoPlay: true,
                    playInterval: 2000,
                    data: timelineDate,
                    currentIndex: currentIndex,
                },
                title: {
                    text: '中国各份平均受教育年限地图',
                    left: 'center'
                },
                tooltip: {
                    trigger: 'item',
                    formatter: '{b}<br/>{c} 年'
                },
                series: [
                    {
                        name: '平均受教育年限',
                        type: 'map',
                        mapType: 'china',
                        roam: false,
                        label: {
                            show: true
                        },
                        data: educationData.map(item => ({
                            name: item.province,
                            value: item.averageEducation
                        })),
                        itemStyle: {
                            emphasis: {
                                areaColor: '#FFD700',
                                borderColor: '#FFFF00',
                                borderWidth: 2
                            }
                        }
                    }
                ],
                visualMap: {
                    min: minEducation,
                    max: maxEducation,
                    left: 'left',
                    top: 'bottom',
                    text: ['高', '低'], // 文本，默认为数值文本
                    calculable: true,
                    inRange: {
                        color: ['#D7DA8B', '#FF4500'] // 颜色映射范围
                    }
                },
            },
            options: [
                {
                    title: {
                        text: '第五次人口普查'
                    },
                },
                {
                    title: {
                        text: '第六次人口普查'
                    },
                },
                {
                    title: {
                        text: '第七次人口普查'
                    },
                }
            ]
        };

        // 使用刚指定的配置项和数据显示地图
        educationMap.setOption(option);
    }

    // 数据轮播
    setInterval(function () {
        currentIndex++;
        if (currentIndex >= timelineData.length) {
            currentIndex = 0; // 循环播放
        }

        var currentData;
        if (currentIndex === 0) {
            currentData = data1;
        } else if (currentIndex === 1) {
            currentData = data2;
        } else {
            currentData = data3;
        }

        handleData(currentData, timelineData);
    }, 2000);

    // 初始化第一组数据
    handleData(data1, timelineData);
</script>

</body>
</html>
