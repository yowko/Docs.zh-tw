---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: eb0475796a488489f4a32c820d1a92994237d7fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a><span data-ttu-id="d3f11-102">&lt;claimsAuthorizationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="d3f11-102">&lt;claimsAuthorizationManager&gt;</span></span>
<span data-ttu-id="d3f11-103">註冊的連入宣告的宣告授權管理員。</span><span class="sxs-lookup"><span data-stu-id="d3f11-103">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="d3f11-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d3f11-104">\<system.identityModel></span></span>  
<span data-ttu-id="d3f11-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d3f11-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d3f11-106">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="d3f11-106">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f11-107">語法</span><span class="sxs-lookup"><span data-stu-id="d3f11-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3f11-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3f11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d3f11-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3f11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3f11-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d3f11-110">Attributes</span></span>  
  
|<span data-ttu-id="d3f11-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d3f11-111">Attribute</span></span>|<span data-ttu-id="d3f11-112">描述</span><span class="sxs-lookup"><span data-stu-id="d3f11-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3f11-113">類型</span><span class="sxs-lookup"><span data-stu-id="d3f11-113">type</span></span>|<span data-ttu-id="d3f11-114">自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別。</span><span class="sxs-lookup"><span data-stu-id="d3f11-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="d3f11-115">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3f11-115">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3f11-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d3f11-116">Child Elements</span></span>  
 <span data-ttu-id="d3f11-117">如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthorizationManager>`項目不接受子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>可以定義子組態項目。</span><span class="sxs-lookup"><span data-stu-id="d3f11-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3f11-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d3f11-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d3f11-119">項目</span><span class="sxs-lookup"><span data-stu-id="d3f11-119">Element</span></span>|<span data-ttu-id="d3f11-120">描述</span><span class="sxs-lookup"><span data-stu-id="d3f11-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3f11-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d3f11-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="d3f11-122">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="d3f11-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3f11-123">備註</span><span class="sxs-lookup"><span data-stu-id="d3f11-123">Remarks</span></span>  
 <span data-ttu-id="d3f11-124">透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthorizationManager>類別一律會授與的連入宣告。</span><span class="sxs-lookup"><span data-stu-id="d3f11-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="d3f11-125">如果沒有`type`指定屬性或`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthorizationManager>類別，`<claimsAuthorizationManager>`項目不接受子項目。</span><span class="sxs-lookup"><span data-stu-id="d3f11-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="d3f11-126">您可以指定`type`屬性註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別來實作自訂行為。</span><span class="sxs-lookup"><span data-stu-id="d3f11-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="d3f11-127">在衍生的類別可以支援透過子項目的組態`<claimsAuthorizationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>方法來處理這些項目。</span><span class="sxs-lookup"><span data-stu-id="d3f11-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="d3f11-128">子項目定義的結構描述是由類別的設計工具。</span><span class="sxs-lookup"><span data-stu-id="d3f11-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3f11-129">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼所參考的身分識別組態中的宣告型存取控制`<federationConfiguration>`項目會設定用來建立原則與 claims authorization manager 授權授權決策。</span><span class="sxs-lookup"><span data-stu-id="d3f11-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="d3f11-130">這是為 true，即使在不是被動 Web 案例，例如 Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="d3f11-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="d3f11-131">如果應用程式不是被動的 Web 應用程式，`<claimsAuthorizationManager>`元素 （和其子原則項目，如果有的話） 的參考的識別組態所套用的唯一設定。</span><span class="sxs-lookup"><span data-stu-id="d3f11-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="d3f11-132">會忽略所有其他設定。</span><span class="sxs-lookup"><span data-stu-id="d3f11-132">All other settings are ignored.</span></span> <span data-ttu-id="d3f11-133">如需詳細資訊，請參閱[ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="d3f11-133">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="d3f11-134">這個項目設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="d3f11-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f11-135">範例</span><span class="sxs-lookup"><span data-stu-id="d3f11-135">Example</span></span>  
 <span data-ttu-id="d3f11-136">下列 XML 顯示宣告授權的組態管理員會實作的原則資源動作配對所組成的每個皆指定布林值的組合，要求者必須擁有在資源上執行動作的宣告。</span><span class="sxs-lookup"><span data-stu-id="d3f11-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="d3f11-137">實作宣告授權管理員能夠使用此原則的程式碼位於`ClaimsBasedAuthorization`範例。</span><span class="sxs-lookup"><span data-stu-id="d3f11-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
