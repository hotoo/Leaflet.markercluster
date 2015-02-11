
# Example

----

<link type="text/css" rel="stylesheet" href="../spm_modules/leaflet/0.7.3/leaflet.css" />
<link type="text/css" rel="stylesheet" href="../markercluster.css" />
<link type="text/css" rel="stylesheet" href="../markercluster.default.css" />

<div id="map-demo" style="height:300px"></div>


````js
seajs.use(['jquery', 'leaflet', 'leaflet.markercluster'], function($, L){

  // 定义 google 地图
  L.tileLayer.google = '';
  L.Icon.Default.imagePath = "/spm_modules/leaflet/0.7.3/images";

  // map
  var map = L.map('map-demo', {
      center: new L.LatLng(37, 120),
      zoom: 4,
      // zoomControl: false,
      fullscreenControl: true,
      layers: L.tileLayer(
        'http://mt{s}.google.cn/vt/lyrs=m&hl=zh-CN&gl=cn&x={x}&y={y}&z={z}', {
          attribution: 'Google',
          subdomains: [0,1,2,3]
        })
  });

  map.attributionControl.setPrefix('');
  // map.addControl(new L.Control.ZoomMin());

  var markersData = [
    [39.9079100000, 116.4160480000, '北京', '689', '320'],
    [39.1337198330, 117.1844111162, '天津', '689', '320'],
    [38.9196580000, 121.6063850000, '大连', '689', '320'],
    [41.8007658637, 123.4371342395, '沈阳', '689', '320'],
    [31.2331580000, 121.4753050000, '上海', '689', '320'],
    [31.2949654967, 120.6031012223, '苏州', '689', '320'],
    [31.5119223133, 120.3685182122, '无锡', '689', '320'],
    [31.6600150000, 120.7601100000, '常熟', '689', '320'],
    [31.3711935070, 120.9789985030, '昆山', '689', '320'],
    [31.1621879176, 120.6696202103, '吴江', '689', '320'],
    [31.3657228055, 119.8186893645, '宜兴', '689', '320']
  ];

  var markers = new L.MarkerClusterGroup();

  $.each(markersData, function(key, value) {
    var marker = new L.Marker(new L.LatLng(value[0], value[1]));
    marker.bindPopup('<p><strong>'+value[2]+'</strong><br>总进店数: 210<br>有效进店数: 189<br>新进店数: 161<br>再次进店: 28<br>意向进店: 19</p>' ,{});
    markers.addLayer(marker);
  });

  map.addLayer(markers);
})
````
