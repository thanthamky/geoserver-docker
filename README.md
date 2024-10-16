# หลักสูตรอบรมเชิงปฏิบัติการผู้ดูแลระบบภูมิสารสนเทศ Geoserver

## ความต้องการระบบ

- Windows, Linux, MacOS
- Docker Engine https://www.docker.com/

## การติดตั้งระบบ

_หมายเหตุ: คำสั่งด้านล่างเป็นคำสั่งสำหรับระบบปฏิบัติการ Linux และ MacOS หากใช้ Windows ให้เปลี่ยน `$(pwd)` เป็น `%CD%`_
```bash
docker run -d -p 80:8080 \
  --mount src="$(pwd)/datadir",target=/opt/geoserver_data/,type=bind \
  --env GEOSERVER_ADMIN_USER=admin \
  --env GEOSERVER_ADMIN_PASSWORD=geoserver \
  --env INSTALL_EXTENSIONS=true \
  --env STABLE_EXTENSIONS="wps,wps-download,excel,ysld,importer,oracle,sqlserver,authkey" \
  --name geoserver \
  docker.osgeo.org/geoserver:2.25.3
  
```
_คำสั่งสำหรับ Windows_
```bash
docker run -d -p 80:8080 \
  --mount src="%CD%/datadir",target=/opt/geoserver_data/,type=bind \
  --env GEOSERVER_ADMIN_USER=admin \
  --env GEOSERVER_ADMIN_PASSWORD=geoserver \
  --env INSTALL_EXTENSIONS=true \
  --env STABLE_EXTENSIONS="wps,wps-download,excel,ysld,importer,oracle,sqlserver,authkey" \
  --name geoserver \
  docker.osgeo.org/geoserver:2.25.3
```


### ตรวจสอบสถานะเซอร์วิส Geoserver

สถานะการทำงานของ container
```bash
docker ps -a
```

เข้าดู log ของ geoserver

```bash
docker logs geoserver
```



### การเข้าใช้งานระบบ

http://localhost/geoserver


### การลบเซอร์วิส Geoserver

```bash
docker rm --force geoserver
```