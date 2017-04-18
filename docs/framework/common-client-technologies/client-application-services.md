---
title: "用戶端應用程式服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式設定, 用戶端應用程式服務"
  - "ASP.NET 服務, 用戶端應用程式服務"
  - "驗證 [ASP.NET], 用戶端應用程式服務"
  - "用戶端應用程式服務"
  - "用戶端應用程式服務, 關於用戶端應用程式服務"
  - "用戶端應用程式, ASP.NET 服務"
  - "認證 [.NET Framework]"
  - "登入 [用戶端應用程式服務]"
  - "設定檔 [ASP.NET], 用戶端應用程式服務"
  - "以角色為基礎的安全性 [.NET Framework], 用戶端應用程式服務"
  - "角色 [.NET Framework], 用戶端應用程式服務"
  - "共用資訊和功能 [用戶端應用程式服務]"
  - "Web 設定 [用戶端應用程式服務]"
  - "Windows 架構的應用程式, 用戶端應用程式服務"
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 用戶端應用程式服務
用戶端應用程式服務可讓您輕鬆地建立使用 Microsoft ASP.NET 2.0 AJAX 擴充功能隨附之 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 登入、角色和設定檔應用程式服務的 Windows 應用程式。  這些服務可讓多個 Web 和 Windows 應用程式從單一伺服器共用使用者資訊和使用者管理功能。  例如，您可以使用這些服務執行下列工作：  
  
-   驗證使用者。  您可以使用驗證服務來確認使用者的身分識別。  
  
-   判斷已驗證使用者的一或多個角色。  您可以根據使用者角色，使用角色服務來變更應用程式的使用者介面。  例如，您可以為系統管理員角色的使用者提供其他功能。  
  
-   在伺服器上儲存及存取每個使用者的應用程式設定。  您可以使用 Web 設定服務 \(也稱為設定檔服務\) 跨多個應用程式和位置共用設定。  
  
 用戶端應用程式服務透過用戶端服務提供者利用 Web 服務擴充性模型，您可以在應用程式組態檔中指定這些服務提供者。  這些服務提供者包含離線功能，可在網路連線無法使用時，使用驗證、角色和設定資料的本機快取。  
  
 如需 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 應用程式服務的詳細資訊，請參閱 [ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md)。  
  
## 在本節中  
 [用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 描述可透過用戶端應用程式服務提供者取得的功能。  
  
 [如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 描述如何使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具啟用及設定應用程式服務。  同時描述 App.config 檔案的對應變更。  
  
 [如何：使用用戶端應用程式服務實作使用者登入](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 描述如何在應用程式設定為使用用戶端驗證 \(Authentication\) 服務提供者時，驗證 \(Validate\) 使用者。  
  
 [逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 描述如何將單一應用程式中的所有用戶端應用程式服務功能結合在一起。  這個逐步解說將提供端對端指引。  例如，其包含有關如何建立 ASP.NET Web 服務應用程式的指示，您可以使用這個應用程式來測試用戶端應用程式服務。  
  
## 參考  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## 請參閱  
 [ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md)   
 [Using Forms Authentication with Microsoft Ajax](../Topic/Using%20Forms%20Authentication%20with%20Microsoft%20Ajax.md)   
 [Using Roles Information with Microsoft Ajax](../Topic/Using%20Roles%20Information%20with%20Microsoft%20Ajax.md)   
 [Using Profile Information with Microsoft Ajax](../Topic/Using%20Profile%20Information%20with%20Microsoft%20Ajax.md)   
 [ASP.NET Authentication](../Topic/ASP.NET%20Authentication.md)   
 [Managing Authorization Using Roles](../Topic/Managing%20Authorization%20Using%20Roles.md)   
 [OLD NIB: Managing Application Settings](http://msdn.microsoft.com/zh-tw/7de3c3bd-e0dc-4e75-a1aa-7b0ecfaac4fc)   
 [應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)