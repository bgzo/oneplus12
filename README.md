# Oneplus12 OxygenOS 本地化 

因为现在 OxgenOS 和 ColorOS 几乎大同小异了，所以直接可以从 ColorOS 上提取安装包，覆盖到 OxgenOS 上来，大部分都可以正常工作，我需要的包含：

1. 钱包（NFC 模拟）：折腾过 `com.yuanwofei.cardemulator.pro`，不能复制加密卡，只能选择安装钱包解决： https://github.com/geniucker-dev/WalletFix4OOS
2. 电话录音：有大侠阿木制作的模块，但是用着有点牛皮藓，不想用，可以使用 https://github.com/kitsumed/ShizuCallRecorder
3. 家人守护：基于 1，我们直接安装【家人守护】+【屏幕共享】，登录账号即可迁移；
4. 微信录音：卸载自带的录音（API 冲突）。然后安装 【录音】+【AI 语音摘要】即可正常录音微信；

> [!NOTE]
> 钱包报错停止运作的时候，需要清空 `/data/system/package_cache/` 里面的数据，然后重启手机，via: [Issues · geniucker-dev/WalletFix4OOS](https://github.com/geniucker-dev/WalletFix4OOS/issues/12)

## AI 语音摘要 + 录音机

使用前需要卸载自带的录音机，因为直接安装的话会报错：

<img width="250" alt="Screenshot_2026-06-13-22-52-49-73_9e8df3d0c7c1f50248b6ee043a653d26" src="https://github.com/user-attachments/assets/6b53c4e8-2ac2-475f-aa3a-3e4a72f07f3a" />

卸载后安装 ColorOS 的录音 `coloros_com.coloros.accessibilityassistant_15.5.64.apk`，就可以看到 AI 语音摘要入口了：

<img width="250" alt="Screenshot_2026-06-14-00-47-16-15_baad026c030f0815c519371ec60f3549" src="https://github.com/user-attachments/assets/cb5f3d26-ce6b-4bfb-b3ee-4cf0e804e998" />

但是点开还是什么都没有：

<img width="250" alt="Screenshot_2026-06-13-23-03-05-38_238273611e768eddd9fd858dafecd6b9" src="https://github.com/user-attachments/assets/5766607b-9078-4848-9e39-a148c7c7a3d6" />

安装第二个包 `coloros_com.oneplus.soundrecorder_16.2.15.apk`，然后我们就可以看到一切正常了：

<img width="250" alt="Screenshot_2026-06-14-00-48-15-67_238273611e768eddd9fd858dafecd6b9" src="https://github.com/user-attachments/assets/0b708af9-2d7c-46e4-9f80-5c9c38e9fcb9" />

现在进行微信通话后，可以正常显示流体云并开启录制。

文件下载 via: https://github.com/bgzo/oneplus12/releases/tag/com.coloros.accessibilityassistant

## 钱包（NFC模拟）

基于 https://github.com/geniucker-dev/WalletFix4OOS ，然后增加 `/data/adb/walletfix/spoof_vars`

```
MODEL=PJD110
```

然后清空 `/data/system/package_cache/` 里面的数据，然后重启手机，登陆国区账号即可正常使用

via: https://github.com/geniucker-dev/WalletFix4OOS/issues/12

## 家人守护

> [!NOTE]
> 基于钱包的模块刷入，ID 相关已经替换为 ColorOS，以下内容都是基于此背景进行展开：

安装下面两个包：

1. `com.coloros.familyguard`
2. `com.coloros.sharescreen`

然后进行账号登陆，就可以正常工作。

缺少屏幕共享会出现如下错误：

<img width="250" alt="Screenshot_2026-06-13-21-42-56-27_9f261658e6ba2311a8b28340baadd458" src="https://github.com/user-attachments/assets/6b026979-27de-4327-aef6-44704c3aea14" />
