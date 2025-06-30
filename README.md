# 世界各国地图json文件集锦

## 文件简介

This project provides two sets of high-quality world map JSON files, specially designed for ECharts mapping. It includes global maps, detailed China maps, and provincial-level maps with high precision, perfect for international data visualization and regional analysis. Whether for global overviews or in-depth exploration of Chinese provinces, these reliable and customizable maps will enhance your data presentations.

本项目提供两套高质量世界地图JSON文件，专为ECharts地图功能优化。包含全球地图、中国详细地图及各省份细分地图，精度高，适合国际数据展示与地区分析。无论是全球视角还是中国省份深度呈现，这些经过验证、可自定义的地图文件都能提升数据可视化效果，为项目增添专业性与便捷性。

## ​Key Features 核心特点​

🌍 Global & China maps 全球及中国地图

🏙 Provincial-level details 省级细分

⚡ ECharts-ready JSON files 适配ECharts

🛠 Customizable & stable 可定制、高稳定

## 使用说明
echart example
```java script
<script>
  // 初始化图表
  const chart = echarts.init(document.getElementById('map-container'));
  
  // 加载并处理GeoJSON
  fetch('world.json')
    .then(response => response.json())
    .then(geoJSON => {
      // 数据清洗
      geoJSON.features.forEach(feature => {
        if (!feature.properties.name) {
          feature.properties.name = 'Unnamed_Region';
          // 或者使用坐标生成唯一ID
          // feature.properties.name = `Region_${feature.geometry.coordinates[0][0][0]}`;
        }
      });

      // 注册地图
      echarts.registerMap('cleanedWorld', geoJSON);
      
      // 设置图表选项
      chart.setOption({
        series: [{
          type: 'map',
          // 和上面注册名保持一致
          map: 'cleanedWorld',
          data: [
            {name: 'China', value: 4369},
            // 其他数据...
          ]
        }]
      });
    })
    .catch(error => console.error('Error:', error));
</script>
```
