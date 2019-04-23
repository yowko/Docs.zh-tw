---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f758fc8e0934f56f9593246497d8aba5084c4a79
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143347"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="36cb3-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="36cb3-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="36cb3-102">表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="36cb3-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="36cb3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="36cb3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="36cb3-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="36cb3-104">\<behaviors></span></span>  
<span data-ttu-id="36cb3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="36cb3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="36cb3-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="36cb3-106">\<behavior></span></span>  
<span data-ttu-id="36cb3-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="36cb3-107">\<serviceCredentials></span></span>  
<span data-ttu-id="36cb3-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="36cb3-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="36cb3-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="36cb3-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36cb3-110">語法</span><span class="sxs-lookup"><span data-stu-id="36cb3-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36cb3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36cb3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36cb3-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="36cb3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36cb3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="36cb3-113">Attributes</span></span>  
 <span data-ttu-id="36cb3-114">無。</span><span class="sxs-lookup"><span data-stu-id="36cb3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36cb3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="36cb3-115">Child Elements</span></span>  
  
|<span data-ttu-id="36cb3-116">項目</span><span class="sxs-lookup"><span data-stu-id="36cb3-116">Element</span></span>|<span data-ttu-id="36cb3-117">描述</span><span class="sxs-lookup"><span data-stu-id="36cb3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36cb3-118">\<add></span><span class="sxs-lookup"><span data-stu-id="36cb3-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|<span data-ttu-id="36cb3-119">加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="36cb3-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36cb3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="36cb3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="36cb3-121">項目</span><span class="sxs-lookup"><span data-stu-id="36cb3-121">Element</span></span>|<span data-ttu-id="36cb3-122">描述</span><span class="sxs-lookup"><span data-stu-id="36cb3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36cb3-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="36cb3-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="36cb3-124">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="36cb3-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36cb3-125">備註</span><span class="sxs-lookup"><span data-stu-id="36cb3-125">Remarks</span></span>  
 <span data-ttu-id="36cb3-126">您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 (Security Token Service，STS) 的聯合應用程式中使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="36cb3-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="36cb3-127">當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="36cb3-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="36cb3-128">如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="36cb3-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
-   <span data-ttu-id="36cb3-129">將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="36cb3-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
-   <span data-ttu-id="36cb3-130">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="36cb3-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="36cb3-131">如需詳細資訊，請參閱<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="36cb3-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="36cb3-132">如需有關使用這個組態項的詳細資訊，請參閱[How to:Federation Service 上設定認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="36cb3-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cb3-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36cb3-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="36cb3-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="36cb3-134">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="36cb3-135">\<add></span><span class="sxs-lookup"><span data-stu-id="36cb3-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [<span data-ttu-id="36cb3-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="36cb3-136">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="36cb3-137">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="36cb3-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="36cb3-138">如何：Federation Service 上設定認證</span><span class="sxs-lookup"><span data-stu-id="36cb3-138">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
