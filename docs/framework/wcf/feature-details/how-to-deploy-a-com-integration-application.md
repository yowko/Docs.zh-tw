---
title: "HOW TO：部署 COM+ 整合應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# HOW TO：部署 COM+ 整合應用程式
撰寫好 COM\+ 整合應用程式後，您可能會想要將它部署在其他機器上。此主題描述如何將 COM\+ 整合應用程式從一部機器移到另一部機器。  
  
### 移動 COM\+ 主控的整合應用程式  
  
1.  請確定兩部機器上都已安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
2.  從機器 A 匯出應用程式。  
  
3.  將應用程式匯入機器 B。  
  
4.  設定應用程式根目錄。根據慣例，根目錄是 %PROGRAMFILES%\/ComPlus Applications\/{AppGUID}。  
  
5.  從機器 A 的應用程式根目錄，將 Application.config 和 Application.manifest 檔案複製到機器 B 的應用程式根目錄。  
  
6.  在機器 B 的 Application.config 檔案中編輯服務端點位址，以識別適當的機器。例如，將 http:\/\/machineA\/MyService 變更為 http:\/\/machineB\/MyService。  
  
### 移動 Web 主控的整合應用程式  
  
1.  請確定兩部機器上都已安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。  
  
2.  從機器 A 匯出應用程式。  
  
3.  將應用程式匯入機器 B。  
  
4.  在機器 B 上建立 IIS VRoot。  
  
5.  從機器 A 的 VRoot，將 .svc 檔 \(componentName.svc\) 和 Web.config 檔複製到機器 B 上新建立的 VRoot。  
  
## 請參閱  
 [整合 COM\+ 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)   
 [HOW TO：設定 COM\+ 服務設定](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)   
 [HOW TO：使用 COM\+ 服務模型組態工具](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)