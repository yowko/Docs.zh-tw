---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252076"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="a0488-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="a0488-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="a0488-102">為傳入宣告註冊宣告授權管理員。</span><span class="sxs-lookup"><span data-stu-id="a0488-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
<span data-ttu-id="a0488-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a0488-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a0488-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="a0488-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="a0488-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a0488-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="a0488-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthorizationManager >**</span><span class="sxs-lookup"><span data-stu-id="a0488-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0488-107">語法</span><span class="sxs-lookup"><span data-stu-id="a0488-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0488-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0488-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a0488-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a0488-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0488-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a0488-110">Attributes</span></span>  
  
|<span data-ttu-id="a0488-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a0488-111">Attribute</span></span>|<span data-ttu-id="a0488-112">描述</span><span class="sxs-lookup"><span data-stu-id="a0488-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0488-113">型別</span><span class="sxs-lookup"><span data-stu-id="a0488-113">type</span></span>|<span data-ttu-id="a0488-114">衍生<xref:System.Security.Claims.ClaimsAuthorizationManager>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="a0488-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="a0488-115">如需如何指定屬性的`type`詳細資訊，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a0488-115">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0488-116">子元素</span><span class="sxs-lookup"><span data-stu-id="a0488-116">Child Elements</span></span>  
 <span data-ttu-id="a0488-117"><xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager>如果沒有`type`屬性，或屬性參考類別，則專案不會採用子項目; 不過，衍生自的類別可以定義子設定元素。 `type`</span><span class="sxs-lookup"><span data-stu-id="a0488-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0488-118">父項目</span><span class="sxs-lookup"><span data-stu-id="a0488-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a0488-119">項目</span><span class="sxs-lookup"><span data-stu-id="a0488-119">Element</span></span>|<span data-ttu-id="a0488-120">描述</span><span class="sxs-lookup"><span data-stu-id="a0488-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0488-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a0488-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="a0488-122">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="a0488-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0488-123">備註</span><span class="sxs-lookup"><span data-stu-id="a0488-123">Remarks</span></span>  
 <span data-ttu-id="a0488-124">透過<xref:System.Security.Claims.ClaimsAuthorizationManager>類別提供的預設行為一律會授權傳入宣告。</span><span class="sxs-lookup"><span data-stu-id="a0488-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="a0488-125">如果未`type`指定任何屬性，或`type`屬性指定了<xref:System.Security.Claims.ClaimsAuthorizationManager>類別，則`<claimsAuthorizationManager>`專案不會採用子項目。</span><span class="sxs-lookup"><span data-stu-id="a0488-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="a0488-126">您可以指定`type`屬性來註冊衍生自類別的<xref:System.Security.Claims.ClaimsAuthorizationManager>型別，以執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="a0488-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="a0488-127">衍生類別可以藉由覆`<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>寫方法來處理這些專案，藉以支援透過專案的子專案進行設定。</span><span class="sxs-lookup"><span data-stu-id="a0488-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="a0488-128">為子專案定義的架構是由類別的設計工具所組成。</span><span class="sxs-lookup"><span data-stu-id="a0488-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0488-129">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>或類別在您的程式碼中提供宣告型存取控制時， `<federationConfiguration>`元素所參考的身分識別設定會設定宣告授權管理員和原則，以用來進行授權決策。</span><span class="sxs-lookup"><span data-stu-id="a0488-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="a0488-130">這也適用于非被動 Web 案例的情況，例如 Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0488-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="a0488-131">如果應用程式不是被動的 Web 應用程式， `<claimsAuthorizationManager>`則會套用所參考身分識別設定的專案（及其子原則元素（如果有的話））。</span><span class="sxs-lookup"><span data-stu-id="a0488-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="a0488-132">所有其他設定都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a0488-132">All other settings are ignored.</span></span> <span data-ttu-id="a0488-133">如需詳細資訊，請參閱[ \<federationConfiguration >](federationconfiguration.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a0488-133">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="a0488-134">這個元素會設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="a0488-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0488-135">範例</span><span class="sxs-lookup"><span data-stu-id="a0488-135">Example</span></span>  
 <span data-ttu-id="a0488-136">下列 XML 顯示宣告授權管理員的設定，其會執行由資源動作配對組成的原則，其中每個都指定要求者必須擁有才能在資源上執行動作的宣告的布林組合。</span><span class="sxs-lookup"><span data-stu-id="a0488-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="a0488-137">`ClaimsBasedAuthorization`範例中可以找到可使用此原則來執行宣告授權管理員的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0488-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
