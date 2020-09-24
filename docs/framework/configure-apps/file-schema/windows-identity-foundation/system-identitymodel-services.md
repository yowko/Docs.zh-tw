---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: e909756a58d5008d917fca84af0e478fc4878d2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156806"
---
# \<system.identityModel.services>

<span data-ttu-id="dd2ca-102">使用 WS-同盟通訊協定進行驗證的設定區段。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="dd2ca-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd2ca-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd2ca-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd2ca-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dd2ca-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd2ca-106">屬性</span><span class="sxs-lookup"><span data-stu-id="dd2ca-106">Attributes</span></span>  

 <span data-ttu-id="dd2ca-107">無</span><span class="sxs-lookup"><span data-stu-id="dd2ca-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd2ca-108">子元素</span><span class="sxs-lookup"><span data-stu-id="dd2ca-108">Child Elements</span></span>  
  
|<span data-ttu-id="dd2ca-109">項目</span><span class="sxs-lookup"><span data-stu-id="dd2ca-109">Element</span></span>|<span data-ttu-id="dd2ca-110">描述</span><span class="sxs-lookup"><span data-stu-id="dd2ca-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="dd2ca-111">包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP 模組的設定。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd2ca-112">父項目</span><span class="sxs-lookup"><span data-stu-id="dd2ca-112">Parent Elements</span></span>  

 <span data-ttu-id="dd2ca-113">None</span><span class="sxs-lookup"><span data-stu-id="dd2ca-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd2ca-114">備註</span><span class="sxs-lookup"><span data-stu-id="dd2ca-114">Remarks</span></span>  

 <span data-ttu-id="dd2ca-115">將 `<system.identityModel.services>` 區段新增至您的應用程式佈建檔，以提供 SAM 和 WSFAM 的設定。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd2ca-116">使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，宣告授權管理員 (<xref:System.Security.Claims.ClaimsAuthorizationManager>) ，以及用來進行授權決策的原則，是透過 `<identityConfiguration>` `<federationConfiguration>` 此區段中的元素隱含或明確參考的元素來設定。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="dd2ca-117">如需詳細資訊，請參閱元素底下的 **備註** [\<federationConfiguration>](federationconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="dd2ca-118">`<system.identityModel.services>`區段是由 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="dd2ca-119">在 `<federationConfiguration>` 區段中設定之子項目的集合是由類別表示 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> 。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd2ca-120">範例</span><span class="sxs-lookup"><span data-stu-id="dd2ca-120">Example</span></span>  

 <span data-ttu-id="dd2ca-121">下列 XML 說明如何將 `<system.identityModel.services>` 區段新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="dd2ca-122">您必須先為 `<system.identityModel.services>` 區段和區段加入區段宣告 `<system.identityModel>` 。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="dd2ca-123"> (當您加入 `<system.identityModel.services>` 區段時，您也應該加入區段的宣告， `<system.identityModel>` 以確保執行時間可以在 `<identityConfiguration>` 必要時建立預設區段。 ) 加入區段宣告之後，您可以在專案下設定同盟驗證設定 `<system.identityModel.services>` 。</span><span class="sxs-lookup"><span data-stu-id="dd2ca-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
