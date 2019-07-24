# video-first-frame
如何获取视频第一张帧
1、视频是同源的，否则需要处理跨域问题
```
    var initialize = function() {
      output = document.getElementById("output");
      video = document.getElementById("video");
      video.addEventListener('loadeddata',captureImage);
    };
 ```
 
2、截取第一帧代码
```
   canvas.getContext('2d').drawImage(video, 0, 0, canvas.width, canvas.height);
 ```
3、创建canvas
```
var captureImage = function() {
      var canvas = document.createElement("canvas");
      canvas.width = video.videoWidth * scale;
      canvas.height = video.videoHeight * scale;
      canvas.getContext('2d').drawImage(video, 0, 0, canvas.width, canvas.height);
      
      img = document.createElement("img");
      img.src = canvas.toDataURL("image/jpeg", 1.0);
      output.appendChild(img);
    };
```
4、poster html5原生属性
  ```
   document.getElementById('video').setAttribute('poster','./cat.jpeg') //设置任意图片第一帧
  ```
