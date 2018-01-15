---
title: "用戶端應用程式服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 597b2d4d37d76ca722ddcebf9fcfeae532f67a00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="client-application-services"></a>用戶端應用程式服務
用戶端應用程式服務可讓您輕鬆建立 Windows 應用程式，這些應用程式使用 Microsoft ASP.NET 2.0 AJAX 擴充功能隨附的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 登入、角色和設定檔應用程式服務。 這些服務可讓多個 Web 和 Windows 應用程式從單一伺服器共用使用者資訊與使用者管理功能。 例如，您可以使用這些服務執行下列工作：  
  
-   驗證使用者。 您可以使用驗證服務來確認使用者的身分識別。  
  
-   判斷已驗證使用者的一或多個角色。 您可以根據使用者角色，使用角色服務來變更應用程式的使用者介面。 例如，您可以為系統管理員角色的使用者提供其他功能。  
  
-   在伺服器上儲存及存取每個使用者的應用程式設定。 您可以使用 Web 設定服務 (也稱為設定檔服務) 跨多個應用程式和位置共用設定。  
  
 用戶端應用程式服務透過用戶端服務提供者利用 Web 服務擴充性模型，您可以在應用程式組態檔中指定這些服務提供者。 這些服務提供者包含離線功能，可在網路連線無法使用時，使用驗證、角色和設定資料的本機快取。  
  
 如需 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 應用程式服務的詳細資訊，請參閱 [ASP.NET 應用程式服務概觀](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)。  
  
## <a name="in-this-section"></a>本節內容  
 [用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 描述可透過用戶端應用程式服務提供者取得的功能。  
  
 [如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 描述如何使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具啟用及設定應用程式服務。 同時描述 App.config 檔案的對應變更。  
  
 [如何：使用用戶端應用程式服務實作使用者登入](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 描述如何在應用程式設定為使用用戶端驗證 (Authentication) 服務提供者時，驗證 (Validate) 使用者。  
  
 [逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 描述如何將單一應用程式中的所有用戶端應用程式服務功能結合在一起。 這個逐步解說將提供端對端指引。 例如，其包含有關如何建立 ASP.NET Web 服務應用程式的指示，您可以使用這個應用程式來測試用戶端應用程式服務。  
  
## <a name="reference"></a>參考資料  
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
  
## <a name="see-also"></a>請參閱  
 [ASP.NET 應用程式服務概觀](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [使用表單驗證搭配 Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [透過 Microsoft Ajax 使用角色資訊](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [透過 Microsoft Ajax 使用設定檔資訊](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET 驗證](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [使用角色管理授權](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)
