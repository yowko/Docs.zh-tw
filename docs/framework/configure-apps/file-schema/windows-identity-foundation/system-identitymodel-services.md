---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 9728f3caee4dba367e4fc4a3e68213b1055cc3d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793779"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="76406-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="76406-102">\<system.identityModel.services></span></span>
<span data-ttu-id="76406-103">使用 WS-同盟通訊協定進行驗證的組態區段。</span><span class="sxs-lookup"><span data-stu-id="76406-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="76406-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="76406-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76406-105">語法</span><span class="sxs-lookup"><span data-stu-id="76406-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76406-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76406-106">Attributes and Elements</span></span>  
 <span data-ttu-id="76406-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="76406-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76406-108">屬性</span><span class="sxs-lookup"><span data-stu-id="76406-108">Attributes</span></span>  
 <span data-ttu-id="76406-109">None</span><span class="sxs-lookup"><span data-stu-id="76406-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76406-110">子元素</span><span class="sxs-lookup"><span data-stu-id="76406-110">Child Elements</span></span>  
  
|<span data-ttu-id="76406-111">項目</span><span class="sxs-lookup"><span data-stu-id="76406-111">Element</span></span>|<span data-ttu-id="76406-112">描述</span><span class="sxs-lookup"><span data-stu-id="76406-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76406-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="76406-113">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="76406-114">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) HTTP 模組。</span><span class="sxs-lookup"><span data-stu-id="76406-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76406-115">父項目</span><span class="sxs-lookup"><span data-stu-id="76406-115">Parent Elements</span></span>  
 <span data-ttu-id="76406-116">None</span><span class="sxs-lookup"><span data-stu-id="76406-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76406-117">備註</span><span class="sxs-lookup"><span data-stu-id="76406-117">Remarks</span></span>  
 <span data-ttu-id="76406-118">新增`<system.identityModel.services>`SAM 和 WSFAM 提供設定您的應用程式組態檔的區段。</span><span class="sxs-lookup"><span data-stu-id="76406-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76406-119">使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼宣告授權管理員中的宣告型存取控制 (<xref:System.Security.Claims.ClaimsAuthorizationManager>) 和用來製作授權決策的原則已透過`<identityConfiguration>`參考項目隱含或明確地從`<federationConfiguration>`在本節中的項目。</span><span class="sxs-lookup"><span data-stu-id="76406-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="76406-120">如需詳細資訊，請參閱**備註**下方[ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="76406-120">For more information, see the **Remarks** under the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="76406-121">`<system.identityModel.services>`一節以<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>類別。</span><span class="sxs-lookup"><span data-stu-id="76406-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="76406-122">子系的集合`<federationConfiguration>`一節中設定的項目由<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="76406-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76406-123">範例</span><span class="sxs-lookup"><span data-stu-id="76406-123">Example</span></span>  
 <span data-ttu-id="76406-124">下列 XML 示範如何加入`<system.identityModel.services>`組態檔的區段。</span><span class="sxs-lookup"><span data-stu-id="76406-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="76406-125">您必須先新增區段宣告兩個`<system.identityModel.services>`一節和`<system.identityModel>`區段。</span><span class="sxs-lookup"><span data-stu-id="76406-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="76406-126">(當您將加入`<system.identityModel.services>`區段中，您應該加入宣告`<system.identityModel>`一節，以確定預設`<identityConfiguration>`可以由執行階段建立區段，如有必要。)已新增區段宣告之後，您可以設定下的聯合的驗證設定`<system.identityModel.services>`項目。</span><span class="sxs-lookup"><span data-stu-id="76406-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
