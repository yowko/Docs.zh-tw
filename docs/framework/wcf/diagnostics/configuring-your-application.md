---
title: "設定您的應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 設定您的應用程式
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會使用 .NET 組態系統，並讓您在機器和應用程式範圍內設定服務。  
  
 由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 定義的組態設定位於 `<system.serviceModel>` 區段群組中。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的詳細資訊，請參閱下列主題：  
  
-   [設定服務](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 應用程式定義的組態設定會定義在 `<appSettings>` 區段群組中。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] .NET 組態檔中應用程式設定的詳細資訊，請參閱  [\<appSettings\>](http://go.microsoft.com/fwlink/?LinkId=95159)。  
  
## 使用組態編輯器  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] [組態編輯器工具 \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 可讓系統管理員和開發人員使用圖形使用者介面建立和修改 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的組態設定。有了這項工具，您可以管理 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結、行為、服務及診斷的設定，而不用直接編輯 XML 組態檔。  
  
## 在 Visual Studio 中編輯組態檔  
 若要在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中編輯 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務專案的組態檔，請以滑鼠右鍵按一下 \[**方案總管**\] 中的此服務專案，然後選擇 \[**編輯 WCF 組態**\] 內容功能表項目。這會啟動[組態編輯器工具 \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。  
  
> [!NOTE]
>  如果您在 \[**方案總管**\] 中以滑鼠右鍵按一下 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務專案的組態檔以進行編輯，就會發現缺少了 \[**編輯 WCF 組態**\] 內容功能表項目。若要解決這個問題，請按一下 \[**工具**\] 功能表，並選擇 \[**WCF 服務組態編輯器**\]。之後，您就可以用滑鼠右鍵按一下組態檔，並使用 \[**編輯 WCF 組態**\] 內容功能表項目。  
  
## 請參閱  
 [組態編輯器工具 \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)   
 [設定服務](../../../../docs/framework/wcf/configuring-services.md)   
 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)