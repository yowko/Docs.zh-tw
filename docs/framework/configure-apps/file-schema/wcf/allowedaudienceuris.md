---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919968"
---
# <a name="allowedaudienceuris"></a><span data-ttu-id="4369d-101">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="4369d-101">\<allowedAudienceUris></span></span>
<span data-ttu-id="4369d-102">表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="4369d-102">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="4369d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4369d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4369d-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4369d-104">\<behaviors></span></span>  
<span data-ttu-id="4369d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4369d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="4369d-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="4369d-106">\<behavior></span></span>  
<span data-ttu-id="4369d-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="4369d-107">\<serviceCredentials></span></span>  
<span data-ttu-id="4369d-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="4369d-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="4369d-109">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="4369d-109">\<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4369d-110">語法</span><span class="sxs-lookup"><span data-stu-id="4369d-110">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4369d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4369d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4369d-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="4369d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4369d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4369d-113">Attributes</span></span>  
 <span data-ttu-id="4369d-114">無。</span><span class="sxs-lookup"><span data-stu-id="4369d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4369d-115">子元素</span><span class="sxs-lookup"><span data-stu-id="4369d-115">Child Elements</span></span>  
  
|<span data-ttu-id="4369d-116">項目</span><span class="sxs-lookup"><span data-stu-id="4369d-116">Element</span></span>|<span data-ttu-id="4369d-117">描述</span><span class="sxs-lookup"><span data-stu-id="4369d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4369d-118">\<add></span><span class="sxs-lookup"><span data-stu-id="4369d-118">\<add></span></span>](add-of-allowedaudienceuris.md)|<span data-ttu-id="4369d-119">加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="4369d-119">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4369d-120">父項目</span><span class="sxs-lookup"><span data-stu-id="4369d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4369d-121">項目</span><span class="sxs-lookup"><span data-stu-id="4369d-121">Element</span></span>|<span data-ttu-id="4369d-122">說明</span><span class="sxs-lookup"><span data-stu-id="4369d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4369d-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="4369d-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="4369d-124">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="4369d-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4369d-125">備註</span><span class="sxs-lookup"><span data-stu-id="4369d-125">Remarks</span></span>  
 <span data-ttu-id="4369d-126">您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 (Security Token Service，STS) 的聯合應用程式中使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="4369d-126">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="4369d-127">當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="4369d-127">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="4369d-128">如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="4369d-128">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="4369d-129">將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="4369d-129">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="4369d-130">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="4369d-130">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="4369d-131">如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="4369d-131">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="4369d-132">如需使用此設定元素的詳細資訊, [請參閱如何:在同盟服務](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)上設定認證。</span><span class="sxs-lookup"><span data-stu-id="4369d-132">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4369d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4369d-133">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="4369d-134">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="4369d-134">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="4369d-135">\<add></span><span class="sxs-lookup"><span data-stu-id="4369d-135">\<add></span></span>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="4369d-136">安全性行為</span><span class="sxs-lookup"><span data-stu-id="4369d-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4369d-137">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="4369d-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4369d-138">如何：在同盟服務上設定認證</span><span class="sxs-lookup"><span data-stu-id="4369d-138">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
