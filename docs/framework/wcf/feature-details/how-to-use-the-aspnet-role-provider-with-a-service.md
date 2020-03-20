---
title: HOW TO：使用 ASP.NET 角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184762"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="a8319-102">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="a8319-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="a8319-103">ASP.NET角色提供程式（與ASP.NET成員提供程式結合）是一項功能，它使ASP.NET開發人員能夠創建網站，允許使用者使用網站創建帳戶，並為授權目的分配角色。</span><span class="sxs-lookup"><span data-stu-id="a8319-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="a8319-104">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="a8319-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="a8319-105">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8319-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="a8319-106">相反，任何提供其憑據（使用者名/密碼組合）的使用者都可以使用該網站及其服務。</span><span class="sxs-lookup"><span data-stu-id="a8319-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="a8319-107">有關應用程式範例，請參閱[成員資格和角色提供程式](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="a8319-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="a8319-108">有關ASP.NET成員資格提供程式功能的詳細資訊，請參閱[：使用ASP.NET成員資格提供程式](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="a8319-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="a8319-109">角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="a8319-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="a8319-110">出於安全目的，Windows 通信基礎 （WCF） 開發人員可以利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="a8319-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="a8319-111">集成到 WCF 應用程式時，使用者必須向 WCF 用戶端應用程式提供使用者名和密碼組合。</span><span class="sxs-lookup"><span data-stu-id="a8319-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="a8319-112">要使 WCF 能夠使用資料庫，必須<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>創建類的實例，將其<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>屬性設置為<xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，並將實例添加到承載服務<xref:System.ServiceModel.ServiceHost>的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a8319-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="a8319-113">配置角色提供程式</span><span class="sxs-lookup"><span data-stu-id="a8319-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="a8319-114">在 Web.config 檔中`system.web`，在<>元素下，添加<>`roleManager`元素並將其`enabled`屬性設置為 。 `true`</span><span class="sxs-lookup"><span data-stu-id="a8319-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="a8319-115">將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="a8319-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="a8319-116">作為<>`roleManager`元素的子項目，添加<>`providers`元素。</span><span class="sxs-lookup"><span data-stu-id="a8319-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="a8319-117">`providers`作為<>元素的子項目，添加一個<>`add`元素，其中將以下屬性設置為適當的值： `name` `type`、`connectionStringName`和`applicationName`， 如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a8319-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="a8319-118">將服務配置為使用角色提供程式</span><span class="sxs-lookup"><span data-stu-id="a8319-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="a8319-119">在 Web.config 檔中，添加[\<一個系統.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a8319-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="a8319-120">將[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)元素添加到<>`system.ServiceModel`元素。</span><span class="sxs-lookup"><span data-stu-id="a8319-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="a8319-121">向`behaviors`[\<<>元素添加服務行為>。](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a8319-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="a8319-122">>元素添加[\<行為](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)並將`name`屬性設置為適當的值。</span><span class="sxs-lookup"><span data-stu-id="a8319-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="a8319-123">將[\<服務授權>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)添加到<>`behavior`元素。</span><span class="sxs-lookup"><span data-stu-id="a8319-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="a8319-124">將 `principalPermissionMode` 屬性設定為 `UseAspNetRoles`。</span><span class="sxs-lookup"><span data-stu-id="a8319-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="a8319-125">將 `roleProviderName` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="a8319-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="a8319-126">下列範例將說明組態片段。</span><span class="sxs-lookup"><span data-stu-id="a8319-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8319-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8319-127">See also</span></span>

- [<span data-ttu-id="a8319-128">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="a8319-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="a8319-129">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="a8319-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
