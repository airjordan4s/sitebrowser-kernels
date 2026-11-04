# SiteBrowser 内核（Linux）

这里只放 SiteBrowser 安装时下载的浏览器内核包（Release 资产），不含源码。

| 版本 | 文件 | 说明 |
| --- | --- | --- |
| chrome_153 (153.0.8010.27) | `chrome_153-linux.tar.gz` | SunBrowser ELF + chromedriver |

## 用法

```bash
SITEBROWSER_KERNEL_URL=https://github.com/airjordan4s/sitebrowser-kernels/releases/download/v153/chrome_153-linux.tar.gz \
SITEBROWSER_KERNEL_SHA256=5579efac14bb50ee376e3912eaf4607bf363185e315e82f9ba0b98c83ec95239 \
bash install.sh <bundle> <host_id> <saas_url> sitebrowser
```

内核为第三方 Chromium 定制构建（SunBrowser），版权归原作者；本仓库仅作自用分发。
