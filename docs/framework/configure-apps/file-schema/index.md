---
title: ".NET Framework 的組態檔結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".NET Framework 應用程式組態, 組態結構描述"
  - "app.config 檔案, 結構描述"
  - "應用程式組態檔, 結構描述"
  - "應用程式開發 [.NET Framework], 結構描述"
  - "組態結構描述 [.NET Framework]"
  - "組態設定 [.NET Framework], 應用程式"
  - "容器標記"
  - "enterprisesec 組態檔"
  - "enterprisesec.config 檔案"
  - "電腦組態檔"
  - "machine.config 檔案"
  - "結構描述組態設定"
  - "結構描述, 組態設定"
  - "安全性 [.NET Framework], 組態檔"
  - "security.config 檔案"
  - "語式正確的 XML"
  - "XML 標記"
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# .NET Framework 的組態檔結構描述
組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。  .NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。  本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。  
  
 如需組態檔之類型、格式和位置的詳細資訊，請參閱文件[設定應用程式](../../../../docs/framework/configure-apps/index.md)。  如果想要直接編輯組態檔，您必須熟悉 XML。  
  
> [!IMPORTANT]
>  組態檔中的 XML 標記和屬性區分大小寫。  
  
## 在本節中  
 [\<configuration\> 項目](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
 描述 `<configuration>` 項目，這個項目是所有組態檔的最上層項目。  
  
 [\<assemblyBinding\> 項目](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)  
 指定位於組態層級的組件繫結原則。  
  
 [\<linkedConfiguration\> 項目](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)  
 指定要包含的組態檔。  
  
 [啟動設定結構描述](../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 描述指定要使用的 Common Language Runtime 版本的項目。  
  
 [執行階段設定結構描述](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 說明設定組件 \(Assembly\) 繫結和執行階段行為的項目。  
  
 [網路設定結構描述](../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 說明指定 .NET Framework 連接至網際網路之方式的項目。  
  
 [密碼編譯設定結構描述](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 說明對應易記演算法名稱至實作密碼編譯演算法之類別的項目。  
  
 [組態區段結構描述](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)  
 說明用來建立和使用自訂設定之組態區段的項目。  
  
 [追蹤和偵錯設定結構描述](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 說明指定追蹤參數和接聽程式 \(Listener\) 的項目。  
  
 [編譯器和語言提供者設定結構描述](../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 描述在指定可用的語言提供者之編譯器組態的項目。  
  
 [應用程式設定結構描述](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)  
 說明可讓 Windows Form 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定的項目。  
  
 [Web 設定結構描述](../../../../docs/framework/configure-apps/file-schema/web/index.md)  
 Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 \(例如 IIS\) 運作的項目。  用於 aspnet.config 檔案。  
  
## 相關章節  
 [Remoting Settings Schema](http://msdn.microsoft.com/zh-tw/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)  
 說明設定實作遠端處理之用戶端和伺服器應用程式的項目。  
  
 [ASP.NET 設定結構描述](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx)  
 描述控制 ASP.NET Web 應用程式之行為的項目。  
  
 [Web Services Settings Schema](http://msdn.microsoft.com/zh-tw/f84d6d55-1add-4eb7-ae46-33df5833ea2e)  
 描述控制 ASP.NET Web 服務和其用戶端之行為的項目。  
  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/zh-tw/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。