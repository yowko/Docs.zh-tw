---
title: '&lt;a d d&gt;'
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: b7a4ae230e9b8788d9ac23147a3fcf21637dadaf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowedaudienceurisgt"></a><span data-ttu-id="a6bcf-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="a6bcf-102">&lt;allowedAudienceUris&gt;</span></span>
<span data-ttu-id="a6bcf-103">表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-103">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="a6bcf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6bcf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6bcf-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-105">\<behaviors></span></span>  
<span data-ttu-id="a6bcf-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a6bcf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a6bcf-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-107">\<behavior></span></span>  
<span data-ttu-id="a6bcf-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a6bcf-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a6bcf-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="a6bcf-110">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-110">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6bcf-111">語法</span><span class="sxs-lookup"><span data-stu-id="a6bcf-111">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6bcf-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6bcf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a6bcf-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a6bcf-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6bcf-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a6bcf-114">Attributes</span></span>  
 <span data-ttu-id="a6bcf-115">無。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6bcf-116">子項目</span><span class="sxs-lookup"><span data-stu-id="a6bcf-116">Child Elements</span></span>  
  
|<span data-ttu-id="a6bcf-117">項目</span><span class="sxs-lookup"><span data-stu-id="a6bcf-117">Element</span></span>|<span data-ttu-id="a6bcf-118">描述</span><span class="sxs-lookup"><span data-stu-id="a6bcf-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6bcf-119">\<add></span><span class="sxs-lookup"><span data-stu-id="a6bcf-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="a6bcf-120">加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-120">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6bcf-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a6bcf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a6bcf-122">項目</span><span class="sxs-lookup"><span data-stu-id="a6bcf-122">Element</span></span>|<span data-ttu-id="a6bcf-123">描述</span><span class="sxs-lookup"><span data-stu-id="a6bcf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6bcf-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="a6bcf-125">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6bcf-126">備註</span><span class="sxs-lookup"><span data-stu-id="a6bcf-126">Remarks</span></span>  
 <span data-ttu-id="a6bcf-127">您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 (Security Token Service，STS) 的聯合應用程式中使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-127">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="a6bcf-128">當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-128">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="a6bcf-129">如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="a6bcf-129">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="a6bcf-130">將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-130">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="a6bcf-131">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-131">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="a6bcf-132">如需詳細資訊，請參閱<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-132">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="a6bcf-133">如需有關如何使用這個組態項目的詳細資訊，請參閱[How to： 設定聯合服務的認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="a6bcf-133">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bcf-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6bcf-134">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [<span data-ttu-id="a6bcf-135">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a6bcf-135">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="a6bcf-136">\<add></span><span class="sxs-lookup"><span data-stu-id="a6bcf-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)  
 [<span data-ttu-id="a6bcf-137">安全性行為</span><span class="sxs-lookup"><span data-stu-id="a6bcf-137">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a6bcf-138">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a6bcf-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a6bcf-139">如何：設定同盟服務的認證</span><span class="sxs-lookup"><span data-stu-id="a6bcf-139">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
