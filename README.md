# openlayer-
这里记录的是oopenlayer5的一些使用心得。
## 一、geoserver的配置问题
### 1.关于跨域问题，在使用geosever发布服务时，由于本地调试时与服务地址不同域的问题，会出现跨域问题，导致服务加载不出来。
  解决方法:在geoserver\WEB-INF\web.xml中，添加如下配置：
  ```
    <filter>
        <filter-name>cross-origin</filter-name>
        <filter-class>org.mortbay.servlets.CrossOriginFilter</filter-class>
        <init-param>
            <param-name>allowedOrigins</param-name>
            <param-value>*</param-value>
        </init-param>
        <init-param>
            <param-name>allowedMethods</param-name>
            <param-value>GET,POST</param-value>
        </init-param>
        <init-param>
            <param-name>allowedHeaders</param-name>
            <param-value>x-requested-with,content-type</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>cross-origin</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
   ```
  PS：新版Geoserver中已有该段代码，只需将此段代码取消注释即可
  
### 2.关于查询要素报错的问题其中一个为，读取jsonp格式报错，是由于未开启加载jsonp格式的配置
    解决方法：在geoserver\WEB-INF\web.xml中，添加或者取消注释如下配置：
  ```
   <context-param>
     <param-name>ENABLE_JSONP</param-name>
     <param-value>true</param-value>
   </context-param>
  ```
### 3.完成后重启服务，即可
## 二、openlayer开发心得
### 目前使用版本为openlayer5，网上的教学版本为openlayer3，推荐一个教程，说的很详细，很基础。
   [ol3教程]:  https://weilin.me/ol3-primer/ 'ol3教程'
 
