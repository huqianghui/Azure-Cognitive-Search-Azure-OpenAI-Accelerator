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

<img width="1139" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/f557c00e-6ff6-4a55-9c13-a6c509436481">

1.	可以通过bot文件，导入。主要是endpoint设定。
   
2.	可以上传文件，或者语音输入
   
3.	通过点击link 查看上面的结果。


4.	在portal上创建bot service，指定自己已经创建的appId 

参考文档：在 Azure 中预配和发布机器人 - Bot Service | Microsoft Learn
az ad app create --display-name "<app-registration-display-name>" --sign-in-audience "AzureADandPersonalMicrosoftAccount"

az ad app credential reset --id "<appId>"

<img width="468" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/531a46ea-5db8-42a7-85db-d9746e81466c">

5. 创建好bot service后，就可以把app ，创建并发布到azure上。

如果需要适用于bot service的app，需要有env和web.config文件。
参考：在 Azure 中预配和发布机器人 - Bot Service | Microsoft Learn
JavaScript	.env	支持用于管理机器人标识的所有三种应用程序类型。
az bot prepare-deploy --lang <language> --code-dir "."

<img width="468" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/d5823f65-0d7b-4ea3-94f8-fe547324bc5c">

6. 发布好了，有对应的endpoint 和 application insight，再来配置bot 服务和app的映射关系。

   <img width="379" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/1871b205-261c-45f5-83ef-6a6c3a819234">

在application insight中Application api key额外生成一个：

<img width="399" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/f27231e3-f712-44be-af16-a9410e295c8c">

7. Web 测试 和 ngrok测试

   <img width="344" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/803b5fe7-8242-4c80-b056-3e799929fd27">

配置ngrok路径来转发远端请求，变成本地突破防火墙(有兼容性问题，一直没跑通)
<img width="369" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/1f3da896-9703-4255-b91f-0e14045b61f8">

8. 加入teams channel

   <img width="326" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/1bb3381e-fb13-4975-8d09-a0968572c53d">

<img width="376" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/31a66c9b-4a1d-4c90-a8d7-ae63a4c7bbbf">

<img width="758" alt="Screenshot 2023-08-28 at 16 24 50" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/9a859ddd-be7b-4e35-ab57-190936313737">

9. Web app developer

    <img width="381" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/c13af8ea-e80f-4832-b576-05ec1740108a">

增加一个index.html,把内容拷贝过去，然后增加一个默认映射
<img width="378" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/27fbba0e-b19f-4a98-96fc-80d865bba8d2">

再次发布这个bot，默认就可以访问了，不再是仅仅一个backend server

<img width="384" alt="image" src="https://github.com/huqianghui/Azure-Cognitive-Search-Azure-OpenAI-Accelerator/assets/7360524/7830380b-5306-4671-9caa-36f326a800de">











