#功能

1.一次在 IBM 的 4个 不同的 Cloud Foundry应用上安装相同配置的Xray（vless+ws）

2.每日定时重启（请更改重启时间，避免相同）

3.仅支持IBM伦敦

4.内存选择64M


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
  

本项目基于 https://github.com/YG-tsj/Xray-IBM-LD 项目修改而来
