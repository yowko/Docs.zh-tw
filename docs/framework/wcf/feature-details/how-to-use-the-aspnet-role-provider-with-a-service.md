---
title: "HOW TO：使用 ASP.NET 角色提供者搭配服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef526ed1f809fad2f07b66629bbc80530b764d65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="fb136-102">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="fb136-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="fb136-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 角色提供者 (以及 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 成員資格提供者) 這項功能可讓 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 開發人員建立網站，以允許使用者在網站中建立帳戶，並允許對使用者指派角色做為授權用途。</span><span class="sxs-lookup"><span data-stu-id="fb136-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="fb136-104">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="fb136-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="fb136-105">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb136-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="fb136-106">相反的，任何使用者只要提供認證 (使用者名稱/密碼組合) 就可以使用該網站與其服務。</span><span class="sxs-lookup"><span data-stu-id="fb136-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="fb136-107">範例應用程式，請參閱[成員資格和角色提供者](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="fb136-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fb136-108">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]成員資格提供者功能，請參閱[How to： 使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="fb136-108"> the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="fb136-109">角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="fb136-109">The role provider feature uses a SQL Server database to store user information.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fb136-110"> 程式開發人員可以針對安全性目的利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="fb136-110"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="fb136-111">當整合至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式時，使用者必須將使用者名稱/密碼組合提供給 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb136-111">When integrated into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="fb136-112">若要啟用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來使用資料庫，您必須建立 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 類別的執行個體，並將其 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性設為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，然後將行為集合的執行個體新增至裝載服務的 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="fb136-112">To enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="fb136-113">若要設定角色提供者</span><span class="sxs-lookup"><span data-stu-id="fb136-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="fb136-114">在 Web.config 檔案中，在 <`system.web`> 項目，加入 <`roleManager`> 項目並設定其`enabled`屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="fb136-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="fb136-115">將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="fb136-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="fb136-116">做為子項 <`roleManager`> 項目，加入 <`providers`> 項目。</span><span class="sxs-lookup"><span data-stu-id="fb136-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="fb136-117">做為子項 <`providers`> 項目，加入 <`add`> 具有下列屬性項目設定為適當值： `name`， `type`， `connectionStringName`，和`applicationName`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fb136-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="fb136-118">若要設定服務使用角色提供者</span><span class="sxs-lookup"><span data-stu-id="fb136-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="fb136-119">在 Web.config 檔案中，加入[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)項目。</span><span class="sxs-lookup"><span data-stu-id="fb136-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="fb136-120">新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)元素 <`system.ServiceModel`> 項目。</span><span class="sxs-lookup"><span data-stu-id="fb136-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="fb136-121">新增[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)至 <`behaviors`> 項目。</span><span class="sxs-lookup"><span data-stu-id="fb136-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="fb136-122">新增[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目並設定`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="fb136-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="fb136-123">新增[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)至 <`behavior`> 項目。</span><span class="sxs-lookup"><span data-stu-id="fb136-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="fb136-124">將 `principalPermissionMode` 屬性設定為 `UseAspNetRoles`。</span><span class="sxs-lookup"><span data-stu-id="fb136-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="fb136-125">將 `roleProviderName` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="fb136-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="fb136-126">下列範例將說明組態片段。</span><span class="sxs-lookup"><span data-stu-id="fb136-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fb136-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb136-127">See Also</span></span>  
 [<span data-ttu-id="fb136-128">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="fb136-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [<span data-ttu-id="fb136-129">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="fb136-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
