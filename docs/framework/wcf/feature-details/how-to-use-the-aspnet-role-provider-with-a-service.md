---
title: HOW TO：使用 ASP.NET 角色提供者搭配服務
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595293"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="b717d-102">HOW TO：使用 ASP.NET 角色提供者搭配服務</span><span class="sxs-lookup"><span data-stu-id="b717d-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="b717d-103">ASP.NET 角色提供者（結合 ASP.NET 成員資格提供者）是一項功能，可讓 ASP.NET 開發人員建立網站，讓使用者可以建立具有網站的帳戶，並獲指派角色供授權之用。</span><span class="sxs-lookup"><span data-stu-id="b717d-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="b717d-104">任何使用者都可以使用這個功能在網站上建立帳戶，並登入以擁有網站與其服務的獨佔存取權。</span><span class="sxs-lookup"><span data-stu-id="b717d-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="b717d-105">這與 Windows 安全性形成對比，因為 Windows 安全性需要使用者有 Windows 網域的帳戶。</span><span class="sxs-lookup"><span data-stu-id="b717d-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="b717d-106">相反地，任何提供其認證（使用者名稱/密碼組合）的使用者都可以使用該網站與其服務。</span><span class="sxs-lookup"><span data-stu-id="b717d-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="b717d-107">如需範例應用程式，請參閱[成員資格和角色提供者](../samples/membership-and-role-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="b717d-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="b717d-108">如需 ASP.NET 成員資格提供者功能的詳細資訊，請參閱[如何：使用 ASP.NET 成員資格提供者](how-to-use-the-aspnet-membership-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="b717d-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="b717d-109">角色提供者功能會使用 SQL Server 資料庫儲存使用者資訊。</span><span class="sxs-lookup"><span data-stu-id="b717d-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="b717d-110">Windows Communication Foundation （WCF）開發人員可以基於安全性目的，利用這些功能。</span><span class="sxs-lookup"><span data-stu-id="b717d-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="b717d-111">當整合到 WCF 應用程式時，使用者必須提供使用者名稱/密碼組合給 WCF 用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="b717d-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="b717d-112">若要讓 WCF 能夠使用資料庫，您必須建立類別的實例 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> ，將其屬性設定 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> ，並將實例加入至裝載服務之的行為集合 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="b717d-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="b717d-113">設定角色提供者</span><span class="sxs-lookup"><span data-stu-id="b717d-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="b717d-114">在 web.config 檔案中，< `system.web` > 元素底下，新增 < > 專案， `roleManager` 並將其 `enabled` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="b717d-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="b717d-115">將 `defaultProvider` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="b717d-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="b717d-116">做為 <> 專案的子系 `roleManager` ，請新增 <`providers`> 元素。</span><span class="sxs-lookup"><span data-stu-id="b717d-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="b717d-117">做為 <> 元素的子系 `providers` ，請新增 <> 專案，並將 `add` 下列屬性設定為適當的值： `name` 、 `type` 、 `connectionStringName` 和 `applicationName` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b717d-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="b717d-118">將服務設定為使用角色提供者</span><span class="sxs-lookup"><span data-stu-id="b717d-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="b717d-119">在 web.config 檔案中，新增 [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="b717d-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="b717d-120">將 [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 元素加入至 <`system.ServiceModel`> 專案。</span><span class="sxs-lookup"><span data-stu-id="b717d-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="b717d-121">將加入 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) 至 <`behaviors`> 元素。</span><span class="sxs-lookup"><span data-stu-id="b717d-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="b717d-122">新增 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="b717d-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="b717d-123">將加入 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 至 <`behavior`> 元素。</span><span class="sxs-lookup"><span data-stu-id="b717d-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="b717d-124">將 `principalPermissionMode` 屬性設定為 `UseAspNetRoles`。</span><span class="sxs-lookup"><span data-stu-id="b717d-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="b717d-125">將 `roleProviderName` 屬性設定為 `SqlRoleProvider`。</span><span class="sxs-lookup"><span data-stu-id="b717d-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="b717d-126">下列範例將說明組態片段。</span><span class="sxs-lookup"><span data-stu-id="b717d-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b717d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b717d-127">See also</span></span>

- [<span data-ttu-id="b717d-128">成員資格和角色提供者</span><span class="sxs-lookup"><span data-stu-id="b717d-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="b717d-129">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="b717d-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
