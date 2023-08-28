### 1. Bot 服务，或者机器人主要是什么场景。它主要解决几个问题：

a.	它首先区分与webapp的事，它主要偏向用于人机交互。

b.	它提供了很多channel的集成，把所有的channel，比如teams，Facebook，微信等都已经提供了方便的开启。

c.	提供了bot framework和SDK便于开发人员进一步定制化。

d.	提供了一些工具，bot framework composer来端到端创建bot服务，以及 bot framework emulator来辅助测试，通过ngrok远程debug。

### 2.	现在公司在新推荐power virtual agent和power platform来构建机器人

***对于我们这种developer，通过vscode，它也提供了很好的脚手架功能，快速创建***


### 3.	个人开发过程

a.	首先通过js框架，生成了一个project，通过本地可以通过node start跑起来，或者debug模式。然后可以通过bot framework emulator来测试。

<img width="1139" alt="Screenshot 2023-08-28 at 16 18 44" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/fe555e83-cc2e-4610-970a-6f48438ad1b6">

<img width="468" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/f557c00e-6ff6-4a55-9c13-a6c509436481">

1.	可以通过bot文件，导入。主要是endpoint设定。
   
2.	可以上传文件，或者语音输入
   
3.	通过点击link 查看上面的结果。


4.	在portal上创建bot service，指定自己已经创建的appId 

参考文档：在 Azure 中预配和发布机器人 - Bot Service | Microsoft Learn
az ad app create --display-name "<app-registration-display-name>" --sign-in-audience "AzureADandPersonalMicrosoftAccount"

az ad app credential reset --id "<appId>"

