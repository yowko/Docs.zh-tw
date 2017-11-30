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
ms.openlocfilehash: 31738e205d0b2b88cbb049607eeb027db873db3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services"></a><span data-ttu-id="56497-102">用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="56497-102">Client Application Services</span></span>
<span data-ttu-id="56497-103">用戶端應用程式服務可讓您輕鬆建立 Windows 應用程式，這些應用程式使用 Microsoft ASP.NET 2.0 AJAX 擴充功能隨附的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 登入、角色和設定檔應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="56497-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="56497-104">這些服務可讓多個 Web 和 Windows 應用程式從單一伺服器共用使用者資訊與使用者管理功能。</span><span class="sxs-lookup"><span data-stu-id="56497-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="56497-105">例如，您可以使用這些服務執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="56497-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="56497-106">驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="56497-106">Authenticate a user.</span></span> <span data-ttu-id="56497-107">您可以使用驗證服務來確認使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="56497-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="56497-108">判斷已驗證使用者的一或多個角色。</span><span class="sxs-lookup"><span data-stu-id="56497-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="56497-109">您可以根據使用者角色，使用角色服務來變更應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="56497-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="56497-110">例如，您可以為系統管理員角色的使用者提供其他功能。</span><span class="sxs-lookup"><span data-stu-id="56497-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="56497-111">在伺服器上儲存及存取每個使用者的應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="56497-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="56497-112">您可以使用 Web 設定服務 (也稱為設定檔服務) 跨多個應用程式和位置共用設定。</span><span class="sxs-lookup"><span data-stu-id="56497-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="56497-113">用戶端應用程式服務透過用戶端服務提供者利用 Web 服務擴充性模型，您可以在應用程式組態檔中指定這些服務提供者。</span><span class="sxs-lookup"><span data-stu-id="56497-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="56497-114">這些服務提供者包含離線功能，可在網路連線無法使用時，使用驗證、角色和設定資料的本機快取。</span><span class="sxs-lookup"><span data-stu-id="56497-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="56497-115">如需 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 應用程式服務的詳細資訊，請參閱 [ASP.NET 應用程式服務概觀](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)。</span><span class="sxs-lookup"><span data-stu-id="56497-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56497-116">本章節內容</span><span class="sxs-lookup"><span data-stu-id="56497-116">In This Section</span></span>  
 [<span data-ttu-id="56497-117">用戶端應用程式服務概觀</span><span class="sxs-lookup"><span data-stu-id="56497-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="56497-118">描述可透過用戶端應用程式服務提供者取得的功能。</span><span class="sxs-lookup"><span data-stu-id="56497-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="56497-119">如何：設定用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="56497-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="56497-120">描述如何使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具啟用及設定應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="56497-120">Describes how to use the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project designer to enable and configuration application services.</span></span> <span data-ttu-id="56497-121">同時描述 App.config 檔案的對應變更。</span><span class="sxs-lookup"><span data-stu-id="56497-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="56497-122">如何：使用用戶端應用程式服務實作使用者登入</span><span class="sxs-lookup"><span data-stu-id="56497-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="56497-123">描述如何在應用程式設定為使用用戶端驗證 (Authentication) 服務提供者時，驗證 (Validate) 使用者。</span><span class="sxs-lookup"><span data-stu-id="56497-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="56497-124">逐步解說：使用用戶端應用程式服務</span><span class="sxs-lookup"><span data-stu-id="56497-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="56497-125">描述如何將單一應用程式中的所有用戶端應用程式服務功能結合在一起。</span><span class="sxs-lookup"><span data-stu-id="56497-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="56497-126">這個逐步解說將提供端對端指引。</span><span class="sxs-lookup"><span data-stu-id="56497-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="56497-127">例如，其包含有關如何建立 ASP.NET Web 服務應用程式的指示，您可以使用這個應用程式來測試用戶端應用程式服務。</span><span class="sxs-lookup"><span data-stu-id="56497-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="56497-128">參考資料</span><span class="sxs-lookup"><span data-stu-id="56497-128">Reference</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="56497-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56497-129">See Also</span></span>  
 [<span data-ttu-id="56497-130">ASP.NET 應用程式服務概觀</span><span class="sxs-lookup"><span data-stu-id="56497-130">ASP.NET Application Services Overview</span></span>](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="56497-131">使用表單驗證搭配 Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="56497-131">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="56497-132">使用角色資訊與 Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="56497-132">Using Roles Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="56497-133">與 Microsoft Ajax 使用設定檔資訊</span><span class="sxs-lookup"><span data-stu-id="56497-133">Using Profile Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="56497-134">ASP.NET 驗證</span><span class="sxs-lookup"><span data-stu-id="56497-134">ASP.NET Authentication</span></span>](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="56497-135">[使用角色管理授權](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="56497-135">[Managing Authorization Using Roles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="56497-136">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="56497-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
