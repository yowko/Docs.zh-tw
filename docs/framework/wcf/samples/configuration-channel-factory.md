---
title: 組態通道處理站
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: ec48743deddd52faed31b4a1a0af365909593414
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187149"
---
# <a name="configuration-channel-factory"></a>組態通道處理站
此範例涵蓋 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方法。 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>允許從中央管理 WCF 用戶端組態。 如果在應用程式網域載入時間之後選取或變更組態，這可能也相當實用。

## <a name="demonstrates"></a>示範
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>討論
 此範例示範如何使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 將特定組態檔加入至用戶端應用程式，而不必使用預設的應用程式組態檔。

 此範例包含二個專案。 第一個專案是簡單服務，執行這個服務可回覆來自用戶端的訊息。 第二個專案是用戶端應用程式，這個應用程式可以針對 Test.config 組態檔使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 建立兩個 <xref:System.Configuration.ExeConfigurationFileMap> 物件，並使用這兩個物件與服務進行通訊。 兩個用戶端都會使用 Test.config 中指定的組態，與服務進行通訊。

 下列程式碼會將自訂組態檔加入至用戶端應用程式。

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1.  系統管理員權限開啟 Visual Studio 2012。

2.  以滑鼠右鍵按一下 ConfigurationChannelFactory 方案 （2 個專案），然後選取**屬性**。

3.  在 **通用屬性**，選取**啟始專案**，然後按一下**多個啟始專案**。

4.  移動**服務**專案的清單中，開頭**動作 'Start'**，然後移動**用戶端**專案之後**服務**專案，也可以搭配**動作 'Start'**，因此**用戶端**之後執行專案**服務**專案。

5.  按一下 **確定**，然後按下 F5 （或 CTRL + F5） 執行範例。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
