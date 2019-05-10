---
title: <add> 的 <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
ms.openlocfilehash: a18305d2981b1a1c8cf56a9dfcbb14ab3ce1ff92
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607217"
---
# <a name="add-of-allowedaudienceuris"></a><span data-ttu-id="bc372-102">\<add> of \<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bc372-102">\<add> of \<allowedAudienceUris></span></span>
<span data-ttu-id="bc372-103">加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="bc372-103">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
 <span data-ttu-id="bc372-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc372-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc372-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="bc372-105">\<behaviors></span></span>  
<span data-ttu-id="bc372-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bc372-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bc372-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bc372-107">\<behavior></span></span>  
<span data-ttu-id="bc372-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bc372-108">\<serviceCredentials></span></span>  
<span data-ttu-id="bc372-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="bc372-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="bc372-110">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bc372-110">\<allowedAudienceUris></span></span>  
<span data-ttu-id="bc372-111">\<新增 > 項目\<a d d ></span><span class="sxs-lookup"><span data-stu-id="bc372-111">\<add> element for \<allowedAudienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc372-112">語法</span><span class="sxs-lookup"><span data-stu-id="bc372-112">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc372-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc372-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bc372-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc372-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc372-115">屬性</span><span class="sxs-lookup"><span data-stu-id="bc372-115">Attributes</span></span>  
  
|<span data-ttu-id="bc372-116">屬性</span><span class="sxs-lookup"><span data-stu-id="bc372-116">Attribute</span></span>|<span data-ttu-id="bc372-117">描述</span><span class="sxs-lookup"><span data-stu-id="bc372-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc372-118">allowedAudienceUri</span><span class="sxs-lookup"><span data-stu-id="bc372-118">allowedAudienceUri</span></span>|<span data-ttu-id="bc372-119">包含目標 URI 的字串，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以該目標 URI 為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="bc372-119">A string that contains a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc372-120">子元素</span><span class="sxs-lookup"><span data-stu-id="bc372-120">Child Elements</span></span>  
 <span data-ttu-id="bc372-121">無。</span><span class="sxs-lookup"><span data-stu-id="bc372-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc372-122">父項目</span><span class="sxs-lookup"><span data-stu-id="bc372-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bc372-123">項目</span><span class="sxs-lookup"><span data-stu-id="bc372-123">Element</span></span>|<span data-ttu-id="bc372-124">描述</span><span class="sxs-lookup"><span data-stu-id="bc372-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc372-125">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bc372-125">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<span data-ttu-id="bc372-126">表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="bc372-126">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc372-127">備註</span><span class="sxs-lookup"><span data-stu-id="bc372-127">Remarks</span></span>  
 <span data-ttu-id="bc372-128">您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 (Security Token Service，STS) 的聯合應用程式中使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="bc372-128">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="bc372-129">當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="bc372-129">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="bc372-130">如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="bc372-130">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="bc372-131">將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="bc372-131">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="bc372-132">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="bc372-132">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="bc372-133">如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。</span><span class="sxs-lookup"><span data-stu-id="bc372-133">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="bc372-134">如需有關使用這個組態項的詳細資訊，請參閱[How to:Federation Service 上設定認證](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="bc372-134">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc372-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc372-135">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [<span data-ttu-id="bc372-136">\<allowedAudienceUris></span><span class="sxs-lookup"><span data-stu-id="bc372-136">\<allowedAudienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)
- [<span data-ttu-id="bc372-137">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="bc372-137">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="bc372-138">安全性行為</span><span class="sxs-lookup"><span data-stu-id="bc372-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="bc372-139">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="bc372-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bc372-140">如何：Federation Service 上設定認證</span><span class="sxs-lookup"><span data-stu-id="bc372-140">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
