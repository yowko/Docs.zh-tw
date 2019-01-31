---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268090"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="46957-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="46957-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="46957-102">註冊的連入宣告的宣告授權管理員。</span><span class="sxs-lookup"><span data-stu-id="46957-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="46957-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="46957-103">\<system.identityModel></span></span>  
<span data-ttu-id="46957-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="46957-104">\<identityConfiguration></span></span>  
<span data-ttu-id="46957-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="46957-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46957-106">語法</span><span class="sxs-lookup"><span data-stu-id="46957-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46957-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46957-107">Attributes and Elements</span></span>  
 <span data-ttu-id="46957-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="46957-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46957-109">屬性</span><span class="sxs-lookup"><span data-stu-id="46957-109">Attributes</span></span>  
  
|<span data-ttu-id="46957-110">屬性</span><span class="sxs-lookup"><span data-stu-id="46957-110">Attribute</span></span>|<span data-ttu-id="46957-111">描述</span><span class="sxs-lookup"><span data-stu-id="46957-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46957-112">類型</span><span class="sxs-lookup"><span data-stu-id="46957-112">type</span></span>|<span data-ttu-id="46957-113">自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別。</span><span class="sxs-lookup"><span data-stu-id="46957-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="46957-114">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="46957-114">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46957-115">子元素</span><span class="sxs-lookup"><span data-stu-id="46957-115">Child Elements</span></span>  
 <span data-ttu-id="46957-116">如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthorizationManager>`項目不會子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>可以定義子組態項目。</span><span class="sxs-lookup"><span data-stu-id="46957-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46957-117">父項目</span><span class="sxs-lookup"><span data-stu-id="46957-117">Parent Elements</span></span>  
  
|<span data-ttu-id="46957-118">項目</span><span class="sxs-lookup"><span data-stu-id="46957-118">Element</span></span>|<span data-ttu-id="46957-119">描述</span><span class="sxs-lookup"><span data-stu-id="46957-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46957-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="46957-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="46957-121">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="46957-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46957-122">備註</span><span class="sxs-lookup"><span data-stu-id="46957-122">Remarks</span></span>  
 <span data-ttu-id="46957-123">透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthorizationManager>類別一律會授與的連入宣告。</span><span class="sxs-lookup"><span data-stu-id="46957-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="46957-124">如果沒有`type`指定屬性或如果`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthorizationManager>類別，`<claimsAuthorizationManager>`項目未採用子元素。</span><span class="sxs-lookup"><span data-stu-id="46957-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="46957-125">您可以指定`type`屬性來註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別來實作自訂行為。</span><span class="sxs-lookup"><span data-stu-id="46957-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="46957-126">在衍生的類別可支援透過子項目的設定`<claimsAuthorizationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>方法來處理這些項目。</span><span class="sxs-lookup"><span data-stu-id="46957-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="46957-127">子項目定義的結構描述是由設計工具的類別。</span><span class="sxs-lookup"><span data-stu-id="46957-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46957-128">使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼所參考的識別組態中的宣告型存取控制`<federationConfiguration>`項目會設定宣告授權管理員和用來進行的原則授權決策。</span><span class="sxs-lookup"><span data-stu-id="46957-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="46957-129">這是為 true，即使在不是被動的 Web 案例，例如 「 Windows Communication Foundation (WCF) 應用程式 」 或 「 不是以 Web 為基礎的應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="46957-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="46957-130">如果應用程式不是被動的 Web 應用程式，`<claimsAuthorizationManager>`元素 （和其子原則項目，如果有的話） 參考的身分識別組態所套用的唯一設定。</span><span class="sxs-lookup"><span data-stu-id="46957-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="46957-131">會忽略所有其他設定。</span><span class="sxs-lookup"><span data-stu-id="46957-131">All other settings are ignored.</span></span> <span data-ttu-id="46957-132">如需詳細資訊，請參閱 < [ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="46957-132">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="46957-133">這個項目設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="46957-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46957-134">範例</span><span class="sxs-lookup"><span data-stu-id="46957-134">Example</span></span>  
 <span data-ttu-id="46957-135">下列 XML 顯示宣告授權的組態管理員，它會實作的原則資源 / 動作配對所組成的每一個都會指定要求者必須擁有在資源上執行動作的宣告布林值的組合。</span><span class="sxs-lookup"><span data-stu-id="46957-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="46957-136">實作宣告授權管理員能夠使用此原則的程式碼可在`ClaimsBasedAuthorization`範例。</span><span class="sxs-lookup"><span data-stu-id="46957-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
