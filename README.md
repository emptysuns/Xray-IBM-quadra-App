# 功能

1.一次在 IBM 的 4个 不同的 Cloud Foundry应用上安装相同配置的Xray（vless+ws）

2.每周定时重启（请更改重启时间，避免相同）

3.内存选择64M

4.IBM达拉斯适用


   | Secrets变量 | 形式 |
  | --------------------- | ----------- |
  | `IBM_CF_USERNAME`       | IBM Cloud 邮箱地址 |
  | `IBM_CF_PASSWORD` | IBM Cloud 邮箱密码 |
  | `IBM_CF_APP_NAME1` | IBM Cloud 应用1程序名 |
  | `IBM_CF_APP_NAME2` | IBM Cloud 应用2程序名 |
  | `IBM_CF_APP_NAME3` | IBM Cloud 应用3程序名 |
  | `IBM_CF_APP_NAME4` | IBM Cloud 应用4程序名 |
  | `V2_UUID` | 自定义UUID码 |
  | `V2_WS_PATH_VLESS` | 填入自定义PATH路径 |
  | `XRAY_DOWNLOAD_URL` | 填入Xray下载链接，如：https://github.com/XTLS/Xray-core/releases/latest/download/Xray-linux-64.zip |
  
  
# 如何进行worker反代，请参考https://www.youtube.com/watch?v=2WGJbtsY6gw

  ## 单鸡worker反代代码
  
      addEventListener(
     "fetch",event => {
     let url=new URL(event.request.url);
     url.hostname="yourdomain.com";
      url.pathname="your_path";
     let request=new Request(url,event.request);
     event. respondWith(
       fetch(request)
      )
     }
     )

## 多鸡worker反代代码（按天轮换使用）

    const Day0 = 'app0.herokuapp.com'
    const Day1 = 'app1.herokuapp.com'
    const Day2 = 'app2.herokuapp.com'
    const Day3 = 'app3.herokuapp.com'
    const Day4 = 'app4.herokuapp.com'
    addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        let day = nd.getDate() % 5;
        if (day === 0) {
            host = Day0
        } else if (day === 1) {
            host = Day1
        } else if (day === 2) {
            host = Day2
        } else if (day === 3){
            host = Day3
        } else if (day === 4){
            host = Day4
        } else {
            host = Day1
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
       }
       )

本项目基于 https://github.com/YG-tsj/Xray-IBM-LD 项目修改而来
