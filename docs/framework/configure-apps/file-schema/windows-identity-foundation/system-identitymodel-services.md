---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152500"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="805db-102">\<系統.身份模型.服務></span><span class="sxs-lookup"><span data-stu-id="805db-102">\<system.identityModel.services></span></span>
<span data-ttu-id="805db-103">使用 WS-聯合協定進行身份驗證的配置部分。</span><span class="sxs-lookup"><span data-stu-id="805db-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="805db-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="805db-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="805db-105">&nbsp;&nbsp;**\<系統.身份模型.服務>**</span><span class="sxs-lookup"><span data-stu-id="805db-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="805db-106">語法</span><span class="sxs-lookup"><span data-stu-id="805db-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="805db-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="805db-107">Attributes and Elements</span></span>  
 <span data-ttu-id="805db-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="805db-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="805db-109">屬性</span><span class="sxs-lookup"><span data-stu-id="805db-109">Attributes</span></span>  
 <span data-ttu-id="805db-110">None</span><span class="sxs-lookup"><span data-stu-id="805db-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="805db-111">子元素</span><span class="sxs-lookup"><span data-stu-id="805db-111">Child Elements</span></span>  
  
|<span data-ttu-id="805db-112">元素</span><span class="sxs-lookup"><span data-stu-id="805db-112">Element</span></span>|<span data-ttu-id="805db-113">描述</span><span class="sxs-lookup"><span data-stu-id="805db-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="805db-114">\<聯合配置></span><span class="sxs-lookup"><span data-stu-id="805db-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="805db-115">包含配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和 （SAM） <xref:System.IdentityModel.Services.SessionAuthenticationModule> HTTP 模組的設置。</span><span class="sxs-lookup"><span data-stu-id="805db-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="805db-116">父項目</span><span class="sxs-lookup"><span data-stu-id="805db-116">Parent Elements</span></span>  
 <span data-ttu-id="805db-117">None</span><span class="sxs-lookup"><span data-stu-id="805db-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="805db-118">備註</span><span class="sxs-lookup"><span data-stu-id="805db-118">Remarks</span></span>  
 <span data-ttu-id="805db-119">向應用程式的`<system.identityModel.services>`設定檔添加一節，以提供 SAM 和 WSFAM 的設置。</span><span class="sxs-lookup"><span data-stu-id="805db-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="805db-120">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類在代碼中提供基於聲明的存取控制時，用於做出授權決策的聲明授權<xref:System.Security.Claims.ClaimsAuthorizationManager>管理器 （ ） 和策略通過從本節中`<identityConfiguration>``<federationConfiguration>`的元素隱式或顯式引用的元素進行配置。</span><span class="sxs-lookup"><span data-stu-id="805db-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="805db-121">有關詳細資訊，請參閱[\<聯合配置>](federationconfiguration.md)元素下的**備註**。</span><span class="sxs-lookup"><span data-stu-id="805db-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="805db-122">該`<system.identityModel.services>`節由類<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>表示。</span><span class="sxs-lookup"><span data-stu-id="805db-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="805db-123">在節中配置的`<federationConfiguration>`子項目的集合由類<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>表示。</span><span class="sxs-lookup"><span data-stu-id="805db-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="805db-124">範例</span><span class="sxs-lookup"><span data-stu-id="805db-124">Example</span></span>  
 <span data-ttu-id="805db-125">以下 XML 演示如何向設定檔添加`<system.identityModel.services>`節。</span><span class="sxs-lookup"><span data-stu-id="805db-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="805db-126">必須首先為`<system.identityModel.services>`節和`<system.identityModel>`節添加節聲明。</span><span class="sxs-lookup"><span data-stu-id="805db-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="805db-127">（添加`<system.identityModel.services>`節時，還應為`<system.identityModel>`節添加聲明，以確保運行時在必要時可以創建預設`<identityConfiguration>`節。添加節聲明後，可以在`<system.identityModel.services>`元素下配置識別身分同盟設置。</span><span class="sxs-lookup"><span data-stu-id="805db-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
