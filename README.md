# openlayer-
这里记录的是oopenlayer5的一些使用心得。

1.关于跨域问题，在使用geosever发布服务时，由于本地调试时与服务地址不同域的问题，会出现跨域问题，导致服务加载不出来。
  解决方法:在geoserver\WEB-INF\web.xml中，添加如下配置：
   <filter>
    <filter-name>CorsFilter</filter-name>
    <filter-class>org.apache.catalina.filters.CorsFilter</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>CorsFilter</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>
  PS：新版Geoserver中已有该段代码，只需将此段代码取消注释即可
  
  2.关于查询要素报错的问题其中一个为，读取jsonp格式报错，是由于未开启加载jsonp格式的配置
    解决方法：在geoserver\WEB-INF\web.xml中，添加或者取消注释如下配置：
    <context-param>
      <param-name>ENABLE_JSONP</param-name>
      <param-value>true</param-value>
    </context-param>
  
