---
title: "Windows Form 的 ClickOnce 部署 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ClickOnce 部署 [Windows Form]"
  - "逐步解說 [Windows Form], ClickOnce 部署"
  - "Windows Form, ClickOnce 部署"
ms.assetid: 1451fce9-1965-4a03-b4d3-831b5fe4ad66
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Windows Form 的 ClickOnce 部署
下列主題描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，您可以使用這項技術輕鬆地將 Windows Form 應用程式部署到用戶端電腦。  
  
## 相關章節  
 [選擇 ClickOnce 部署策略](../Topic/Choosing%20a%20ClickOnce%20Deployment%20Strategy.md)  
 顯示部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。  
  
 [選擇 ClickOnce 更新策略](../Topic/Choosing%20a%20ClickOnce%20Update%20Strategy.md)  
 顯示更新 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的幾個選項。  
  
 [保護 ClickOnce 應用程式](../Topic/Securing%20ClickOnce%20Applications.md)  
 說明 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的安全性影響。  
  
 [疑難排解 ClickOnce 部署](../Topic/Troubleshooting%20ClickOnce%20Deployments.md)  
 描述在部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式時可能發生的各種問題，並記載 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 可能產生的最上層錯誤訊息。  
  
 [ClickOnce 和應用程式設定](../Topic/ClickOnce%20and%20Application%20Settings.md)  
 描述 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署如何使用應用程式設定，這些設定會儲存應用程式和使用者設定以供未來擷取。  
  
 [受信任的應用程式部署概觀](../Topic/Trusted%20Application%20Deployment%20Overview.md)  
 描述允許信任的應用程式在用戶端電腦上以更高層級的權限執行的 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 功能。  
  
 [ClickOnce 和 Authenticode](../Topic/ClickOnce%20and%20Authenticode.md)  
 描述如何在信任的應用程式部署中使用 Authenticode 技術。  
  
 [逐步解說：手動部署 ClickOnce 應用程式](../Topic/Walkthrough:%20Manually%20Deploying%20a%20ClickOnce%20Application.md)  
 示範如何使用命令列和 SDK 工具來部署 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]，而不使用 Visual Studio。  
  
 [如何：新增信任發行者至 ClickOnce 應用程式的用戶端電腦](../Topic/How%20to:%20Add%20a%20Trusted%20Publisher%20to%20a%20Client%20Computer%20for%20ClickOnce%20Applications.md)  
 示範信任的應用程式部署所需之用戶端電腦的一次組態。  
  
 [如何：指定部署更新的其他位置](../Topic/How%20to:%20Specify%20an%20Alternate%20Location%20for%20Deployment%20Updates.md)  
 示範如何使用 SDK 工具設定 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式，來檢查其他位置是否有新版應用程式。  
  
 [逐步解說：依 ClickOnce 部署 API 的要求下載組件](../Topic/Walkthrough:%20Downloading%20Assemblies%20on%20Demand%20with%20the%20ClickOnce%20Deployment%20API.md)  
 示範如何使用應用程式開發介面呼叫，在應用程式第一次嘗試載入組件時擷取組件。  
  
 [如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊](../Topic/How%20to:%20Retrieve%20Query%20String%20Information%20in%20an%20Online%20ClickOnce%20Application.md)  
 示範如何從用來執行 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的 URL 擷取參數。  
  
 [ClickOnce 快取概觀](../Topic/ClickOnce%20Cache%20Overview.md)  
 描述本機電腦上用來儲存 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式的快取。  
  
 [在 ClickOnce 應用程式中存取本機和遠端資料](../Topic/Accessing%20Local%20and%20Remote%20Data%20in%20ClickOnce%20Applications.md)  
 描述如何從 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 應用程式存取本機資料檔案和遠端資料來源。  
  
 [如何：在 ClickOnce 應用程式中納入資料檔案](../Topic/How%20to:%20Include%20a%20Data%20File%20in%20a%20ClickOnce%20Application.md)  
 示範如何標記檔案，以便在 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 資料目錄中使用。  
  
## 請參閱  
 [應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [發行 ClickOnce 應用程式](../Topic/Publishing%20ClickOnce%20Applications.md)   
 [從命令列建置 ClickOnce 應用程式](../Topic/Building%20ClickOnce%20Applications%20from%20the%20Command%20Line.md)   
 [偵錯使用 System.Deployment.Application 的 ClickOnce 應用程式](../Topic/Debugging%20ClickOnce%20Applications%20That%20Use%20System.Deployment.Application.md)   
 [使用 ClickOnce 部署 COM 元件](../Topic/Deploying%20COM%20Components%20with%20ClickOnce.md)   
 [如何：使用發行精靈發行 ClickOnce 應用程式](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)