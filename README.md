# openlayer-
这里记录的是oopenlayer5的一些使用心得。

1.关于跨域问题，在使用geosever发布服务时，由于本地调试时与服务地址不同域的问题，会出现跨域问题，导致服务加载不出来。
  解决方法:在geoserver中，更改两个位置，分别解决wms和wfs的跨域问题，在geoserver\WEB-INF\web.xml中，修改
