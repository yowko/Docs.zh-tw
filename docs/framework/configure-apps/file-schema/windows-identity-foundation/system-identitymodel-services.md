---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e9488c0681e1a5f0fe94112a36b65ec73bf9fd09
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251814"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="d4c93-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="d4c93-102">\<system.identityModel.services></span></span>
<span data-ttu-id="d4c93-103">使用 WS-同盟通訊協定進行驗證的設定區段。</span><span class="sxs-lookup"><span data-stu-id="d4c93-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="d4c93-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4c93-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4c93-105">&nbsp;&nbsp; **\<Microsoft.identitymodel >**</span><span class="sxs-lookup"><span data-stu-id="d4c93-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c93-106">語法</span><span class="sxs-lookup"><span data-stu-id="d4c93-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4c93-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d4c93-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d4c93-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d4c93-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4c93-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d4c93-109">Attributes</span></span>  
 <span data-ttu-id="d4c93-110">無</span><span class="sxs-lookup"><span data-stu-id="d4c93-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4c93-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d4c93-111">Child Elements</span></span>  
  
|<span data-ttu-id="d4c93-112">項目</span><span class="sxs-lookup"><span data-stu-id="d4c93-112">Element</span></span>|<span data-ttu-id="d4c93-113">說明</span><span class="sxs-lookup"><span data-stu-id="d4c93-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4c93-114">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d4c93-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="d4c93-115">包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) HTTP 模組的設定。</span><span class="sxs-lookup"><span data-stu-id="d4c93-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4c93-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d4c93-116">Parent Elements</span></span>  
 <span data-ttu-id="d4c93-117">None</span><span class="sxs-lookup"><span data-stu-id="d4c93-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4c93-118">備註</span><span class="sxs-lookup"><span data-stu-id="d4c93-118">Remarks</span></span>  
 <span data-ttu-id="d4c93-119">`<system.identityModel.services>`將區段新增至應用程式的設定檔, 以提供 SAM 和 WSFAM 的設定。</span><span class="sxs-lookup"><span data-stu-id="d4c93-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4c93-120">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.Security.Claims.ClaimsAuthorizationManager>或類別在您的程式碼中提供宣告型存取控制時, 宣告授權管理員 () 和用`<identityConfiguration>`來進行授權決策的原則會透過<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>從這個區段的`<federationConfiguration>`元素隱含或明確參考的專案。</span><span class="sxs-lookup"><span data-stu-id="d4c93-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="d4c93-121">如需詳細資訊, 請參閱[ \<federationConfiguration >](federationconfiguration.md)元素底下的**備註**。</span><span class="sxs-lookup"><span data-stu-id="d4c93-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="d4c93-122">`<system.identityModel.services>`區段是<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="d4c93-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="d4c93-123">區段中所設定`<federationConfiguration>`之子專案的集合是<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="d4c93-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c93-124">範例</span><span class="sxs-lookup"><span data-stu-id="d4c93-124">Example</span></span>  
 <span data-ttu-id="d4c93-125">下列 XML 顯示如何將`<system.identityModel.services>`區段新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="d4c93-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="d4c93-126">您必須先為`<system.identityModel.services>`區段`<system.identityModel>`和區段新增區段宣告。</span><span class="sxs-lookup"><span data-stu-id="d4c93-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="d4c93-127">(當您新增`<system.identityModel.services>`區段時, 您也應該新增`<system.identityModel>`區段的宣告, 以確保執行時間可以視`<identityConfiguration>`需要建立預設區段)。新增區段宣告之後, 您可以在`<system.identityModel.services>`元素下設定同盟驗證設定。</span><span class="sxs-lookup"><span data-stu-id="d4c93-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"   
        issuer="http://localhost:15839/wsFederationSTS/Issue"   
        realm="http://localhost:50969/" reply="http://localhost:50969/"   
        requireHttps="false"   
        signOutReply="http://localhost:50969/SignedOutPage.html"   
        signOutQueryString="Param1=value2&Param2=value2"   
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
