---
title: 用戶端應用程式服務概觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- client application services, classes
- client application services, about client application services
ms.assetid: f0a2da13-e282-4fd7-88a1-f9102c9aeab1
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ddc1b505146e7ca31bca5acc5e9d19d258a860d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="client-application-services-overview"></a>用戶端應用程式服務概觀
用戶端應用程式服務簡化了從 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式對 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 登入、角色和設定檔服務的存取。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 應用程式服務隨附於 [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] 和 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] 的 Microsoft ASP.NET 2.0 AJAX Extensions 中。 這些服務可讓多個 Web 和 Windows 應用程式從單一伺服器共用使用者資訊與使用者管理功能。  
  
 用戶端應用程式服務包含可以插入 Web 服務擴充性模型的用戶端服務提供者，讓 Windows 應用程式能夠提供下列功能：  
  
-   簡化用戶端設定。 您可以使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具或在專案的 App.config 檔案中指定用戶端服務提供者，以啟用及設定登入、角色和設定檔服務。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。  
  
-   簡單的程式設計功能。 啟用及設定用戶端應用程式服務之後，您可以透過現有 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 成員資格、角色和應用程式設定類別，間接地存取服務提供者。 您也可以直接存取實作用戶端應用程式服務的 [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] 類別。 但在大部分情況下，直接存取並非必要。 如需用戶端應用程式服務類別的詳細資訊，請參閱本主題的＜用戶端應用程式服務類別＞一節。  
  
-   離線支援。 Windows 應用程式經常需要在偶爾才能連線的環境中運作。 當您的應用程式在線上時，用戶端服務提供者會快取從伺服器擷取的值，供應用程式離線時使用。  
  
-   與 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 應用程式設定設計工具整合。 當您將設定加入您在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 的專案中時，您可以指定哪些設定要透過用戶端設定服務提供者存取。  
  
 下列章節將詳述這些功能。 如需 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 應用程式服務的詳細資訊，請參閱 [ASP.NET 應用程式服務概觀](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)。  
  
## <a name="authentication"></a>驗證  
 您可以透過現有 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 驗證服務，使用用戶端應用程式服務來驗證使用者。 您可以使用 Windows 或表單驗證來驗證使用者。 Windows 驗證表示使用者登入電腦或網域時，是使用作業系統所提供的使用者識別。 通常您會對部署在公司內部網路上的應用程式使用 Windows 驗證。 表單驗證表示您必須在應用程式中加入登入控制項，並將取得的認證傳遞給驗證提供者。 通常您會對部署在網際網路上的應用程式使用表單驗證。  
  
 若要驗證使用者，請呼叫 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> 方法。 此方法會存取應用程式所設定的用戶端服務提供者，並傳回 <xref:System.Boolean> 值，指出使用者是否有效。 如需詳細資訊，請參閱[如何：使用用戶端應用程式服務實作使用者登入](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)。  
  
 使用 Windows 驗證時，您必須傳遞空字串或 `null` 做為 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法的參數。 使用 Windows 驗證時，此方法呼叫一律會傳回 `true`。  
  
 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法會使用表單驗證傳回值，指出遠端服務是否已驗證使用者。 若驗證成功，驗證 cookie 會儲存在本機硬碟上。 在存取角色和設定服務時，會使用此 Cookie 來確認驗證。  
  
 使用表單驗證時，您可以將使用者名稱和密碼傳遞給 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法。 您也可以傳遞空字串或 `null` 做為使用認證提供者的參數。 認證提供者是您在應用程式組態中所提供和指定的類別。 認證提供者類別必須實作具有名為 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 單一方法的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面。 您可透過使用認證提供者在多個應用程式之間分享單一登入對話方塊。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。  
  
 當您設定應用程式使用具有表單驗證的認證提供者時，必須傳遞空字串或 `null` 做為 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法的參數。 服務提供者會接著呼叫您的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> 方法實作。 一般而言，您會實作此方法來顯示對話方塊，並傳回填入的 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> 物件。  
  
 如需驗證的詳細資訊，請參閱 [ASP.NET 驗證](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)。 如需如何設定 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 驗證服務的資訊，請參閱[透過 Microsoft Ajax 使用表單驗證](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)。  
  
## <a name="roles"></a>角色  
 您可以使用用戶端應用程式服務，從現有的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 角色服務擷取角色資訊。 若要判斷目前已經過驗證的使用者是否具有特定角色，可呼叫擷取自 `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性之 <xref:System.Security.Principal.IPrincipal> 參考的 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法 。 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法會以角色名稱作為參數，並傳回 <xref:System.Boolean> 值，指出目前的使用者是否為指定的角色。 若使用者尚未經過驗證，或不是指定的角色，此方法會傳回 `false`。  
  
 如需如何設定 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 角色服務的相關資訊，請參閱[透過 Microsoft Ajax 使用角色資訊](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)。  
  
## <a name="settings"></a>設定  
 您可以利用用戶端服務，從現有的 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務擷取使用者應用程式設定。 用戶端應用程式服務的 Web 設定功能，會與 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 中所提供的應用程式設定功能相整合。 若要擷取 Web 設定，請先使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具的 [設定] 索引標籤，為您的專案產生 `Settings` 類別 (在 C# 中以 `Properties.Settings.Default` 存取，在 Visual Basic 中以 `My.Settings` 存取)。 在 [設定] 索引標籤上，您可以使用 [載入 Web 設定] 按鈕，擷取 Web 設定並將其加入所產生的 `Settings` 類別。 您可以使用設定要供所有經過驗證的使用者或所有匿名使用者使用的 Web 設定。  
  
 如需應用程式設定的詳細資訊，請參閱[應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)。 如需如何實作您自己的設定類別，而不是如何在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中產生此設定類別的相關資訊，請參閱[如何：建立應用程式設定](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。 如需如何設定 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 設定檔服務的相關資訊，請參閱[透過 Microsoft Ajax 使用設定檔資訊](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)。  
  
## <a name="client-application-services-classes"></a>用戶端應用程式服務類別  
 下列資料表描述實作用戶端應用程式服務功能的類別。  
  
 僅使用主要驗證、角色和設定功能的應用程式，無須直接存取這些類別。 相反地，這類應用程式會使用應用程式組態，以及前文中所述的 API 來間接存取用戶端應用程式服務提供者。 您將會直接存取這些類別以實作其他功能，例如使用者登出及離線功能。  
  
> [!NOTE]
>  所有的用戶端應用程式服務 API 均為同步。 用戶端應用程式服務不直接支援非同步行為。  
  
 用戶端應用程式服務提供者實作或擴充標準 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 型別，但不實作這些型別所定義的每個成員和功能。 例如，您無法使用用戶端應用程式服務提供者，實作用以建立新使用者和管理角色成員資格的使用者管理應用程式。 若要實作這項功能，您必須已在使用 Web 應用程式和伺服器端程式碼。 若要判斷哪些成員尚未實作，請參閱參考文件。您可以從這份資料表中的連結來存取這份參考文件。  
  
|類別|描述|  
|-----------|-----------------|  
|<xref:System.Web.ClientServices.ClientFormsIdentity>|此類別會管理表單驗證的使用者識別身分與驗證 Cookie。<br /><br /> 直接存取此類別的主要原因是呼叫 <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> 方法，它以無訊息方式重新驗證使用者 (例如，從離線模式切換成線上模式時)。<br /><br /> 使用表單驗證來驗證使用者之後，您可以透過擷取自 `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性之 <xref:System.Security.Principal.IPrincipal> 參考的 <xref:System.Security.Principal.IPrincipal.Identity%2A> 屬性來擷取此類別的執行個體。|  
|<xref:System.Web.ClientServices.ClientRolePrincipal>|此類別會管理使用者角色。<br /><br /> 此類別沒有任何無法間接存取的成員。 不過，驗證使用者之後，您可以透過 `static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性存取此類別的執行個體。|  
|<xref:System.Web.ClientServices.ConnectivityStatus>|此類別會提供您用於將應用程式切換到離線模式的 `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> 屬性。|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>|此類別代表使用者認證。<br /><br /> 當您實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面時，您將只會使用此類別做為 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法的傳回值類型。|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>|此類別會管理表單驗證的遠端驗證服務存取權。<br /><br /> 直接存取此類別的主要原因，在利用其 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> 和 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> 成員，而基底 <xref:System.Web.Security.MembershipProvider> 類別並未實作這兩個成員。 您也可以使用 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.ServiceUri%2A> 屬性，以程式設計方式來設定服務位置。<br /><br /> 您可以透過 `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> 屬性擷取此類別的執行個體。|  
|<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>|此類別會管理 Windows 驗證。<br /><br /> 直接存取此類別的主要原因是呼叫其 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider.Logout%2A> 方法。 登出後，使用者仍然會於 Windows 驗證，但無法存取遠端應用程式服務。<br /><br /> 您可以透過 `static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> 屬性擷取此類別的執行個體。|  
|<xref:System.Web.ClientServices.Providers.ClientRoleProvider>|此類別會管理遠端角色服務的存取權。<br /><br /> 直接存取此類別的主要原因是呼叫其 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> 方法。 如果您的應用程式設定為使用非零的角色服務快取逾時值，這會非常有用。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。 您也可以使用 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ServiceUri%2A> 屬性，以程式設計方式來設定服務位置。<br /><br /> 您可以透過 `static` <xref:System.Web.Security.Roles.Provider%2A?displayProperty=nameWithType> 屬性擷取此類別的執行個體。|  
|<xref:System.Web.ClientServices.Providers.ClientSettingsProvider>|此類別會管理遠端 Web 設定服務的存取權。<br /><br /> 直接存取此類別的主要原因是處理 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件。 您也可以使用 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.ServiceUri%2A> 屬性，以程式設計方式來設定服務位置。|  
|<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>|如前面本主題的 [驗證] 區段中所述，此介面會為您的應用程式提供間接取得使用者認證以進行驗證的方式。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。|  
|<xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>|此類別會提供用於 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> 事件處理常式的 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs.FailedSettingsList%2A> 屬性。|  
|<xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>|此類別會提供用於 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> 事件處理常式的 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs.UserName%2A> 屬性。|  
  
## <a name="see-also"></a>請參閱  
 [用戶端應用程式服務](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [操作說明：使用用戶端應用程式服務實作使用者登入](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [逐步解說：使用用戶端應用程式服務](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [應用程式設定概觀](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ASP.NET 應用程式服務概觀](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [使用表單驗證搭配 Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [透過 Microsoft Ajax 使用角色資訊](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [透過 Microsoft Ajax 使用設定檔資訊](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET 驗證](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [使用角色管理授權](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  
 [建立及設定 SQL Server 的應用程式服務資料庫](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
