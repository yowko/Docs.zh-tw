---
title: "設定通道處理站 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 設定通道處理站
此範例涵蓋 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 的使用方法。<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 允許從中央管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組態。如果在應用程式網域載入時間之後選取或變更組態，這可能也相當實用。  
  
## 示範  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## 討論  
 此範例示範如何使用 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 將特定組態檔加入至用戶端應用程式，而不必使用預設的應用程式組態檔。  
  
 此範例包含二個專案。第一個專案是簡單服務，執行這個服務可回覆來自用戶端的訊息。第二個專案是用戶端應用程式，這個應用程式可以針對 Test.config 組態檔使用 <xref:System.Configuration.ExeConfigurationFileMap> 建立兩個 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> 物件，並使用這兩個物件與服務進行通訊。兩個用戶端都會使用 Test.config 中指定的組態，與服務進行通訊。  
  
 下列程式碼會將自訂組態檔加入至用戶端應用程式。  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
  
```  
  
#### 若要安裝、建立及執行範例  
  
1.  以系統管理員權限開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  以滑鼠右鍵按一下 ConfigurationChannelFactory 方案 \(2 個專案\)，然後選取 \[**屬性**\]。  
  
3.  選取 \[**通用屬性**\] 中的 \[**啟始專案**\]，然後按一下 \[**多個啟始專案**\]。  
  
4.  使用 \[**動作 \[開始\]**\] 將 \[**服務**\] 專案移到清單的開頭，然後同樣使用 \[**動作 \[開始\]**\] 將 \[**用戶端**\] 專案移到 \[**服務**\] 專案後面，如此 \[**用戶端**\] 專案就會在 \[**服務**\] 專案之後執行。  
  
5.  按一下 \[**確定**\]，然後按下 F5 \(或 CTRL\+F5\) 以執行範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`