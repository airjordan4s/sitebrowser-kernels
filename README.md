# SiteBrowser 内核

这里只放 SiteBrowser 安装 / 导入时使用的浏览器内核包（Release 资产），不含源码。

| 平台 | 版本 | 文件 | 说明 |
| --- | --- | --- | --- |
| Linux | chrome_153 (153.0.8010.27) | `chrome_153-linux.tar.gz` | SunBrowser ELF + chromedriver |
| Windows | chrome_153 (153.0.8010.27) | `chrome_153-win.tar.gz` | SunBrowser.exe + chrome.dll + chromedriver.exe |

## Linux 用法

```bash
SITEBROWSER_KERNEL_URL=https://github.com/airjordan4s/sitebrowser-kernels/releases/download/v153/chrome_153-linux.tar.gz \
SITEBROWSER_KERNEL_SHA256=5579efac14bb50ee376e3912eaf4607bf363185e315e82f9ba0b98c83ec95239 \
bash install.sh <bundle> <host_id> <saas_url> sitebrowser
```

## Windows 用法

```powershell
# 1) 下载并校验
curl.exe -L -o "$env:TEMP\chrome_153-win.tar.gz" https://github.com/airjordan4s/sitebrowser-kernels/releases/download/v153/chrome_153-win.tar.gz
(Get-FileHash "$env:TEMP\chrome_153-win.tar.gz" -Algorithm SHA256).Hash   # 应为 666e8f00aa98abdfef73060dbf3b48f8eb43a9f10f7eae309a9df3c620454963

# 2) 解到内核目录（解出 chrome_153\ 一层）
tar -xzf "$env:TEMP\chrome_153-win.tar.gz" -C D:\SiteBrowserKernels

# 3) 核对清单
powershell -File tools\import-kernel.ps1 -ManifestOnly
```

解包后目录结构：`D:\SiteBrowserKernels\chrome_153\SunBrowser.exe` + `chrome_153\153.0.8010.27\chrome.dll`。

| 文件 | SHA256 |
| --- | --- |
| `chrome_153-win.tar.gz` | `666e8f00aa98abdfef73060dbf3b48f8eb43a9f10f7eae309a9df3c620454963` |
| `chrome_153\153.0.8010.27\chrome.dll` | `A56B50939BD47D59A67805CC087E31D6B7E8C22BBBCD492DD89FF7497C42F22E` |
| `chrome_153-linux.tar.gz` | `5579efac14bb50ee376e3912eaf4607bf363185e315e82f9ba0b98c83ec95239` |

内核为第三方 Chromium 定制构建（SunBrowser，签名者 SUNFLOWER TECH PTE. LTD.），版权归原作者；本仓库仅作自用分发。
