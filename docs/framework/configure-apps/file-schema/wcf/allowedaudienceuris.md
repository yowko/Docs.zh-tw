---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: ea2d4bb285047939992e9b191abc2dc896bdaa6a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398280"
---
# \<allowedAudienceUris>
<span data-ttu-id="8bfa7-101">表示目標 URI 的集合，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-101">Represents a collection of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowedAudienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="8bfa7-102">語法</span><span class="sxs-lookup"><span data-stu-id="8bfa7-102">Syntax</span></span>  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bfa7-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8bfa7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="8bfa7-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="8bfa7-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bfa7-105">屬性</span><span class="sxs-lookup"><span data-stu-id="8bfa7-105">Attributes</span></span>  
 <span data-ttu-id="8bfa7-106">無。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8bfa7-107">子元素</span><span class="sxs-lookup"><span data-stu-id="8bfa7-107">Child Elements</span></span>  
  
|<span data-ttu-id="8bfa7-108">元素</span><span class="sxs-lookup"><span data-stu-id="8bfa7-108">Element</span></span>|<span data-ttu-id="8bfa7-109">描述</span><span class="sxs-lookup"><span data-stu-id="8bfa7-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|<span data-ttu-id="8bfa7-110">加入目標 URI，<xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖會以其為目標，這樣 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 執行個體才會將其視為有效。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-110">Adds a target Uri for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8bfa7-111">父項目</span><span class="sxs-lookup"><span data-stu-id="8bfa7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8bfa7-112">元素</span><span class="sxs-lookup"><span data-stu-id="8bfa7-112">Element</span></span>|<span data-ttu-id="8bfa7-113">描述</span><span class="sxs-lookup"><span data-stu-id="8bfa7-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="8bfa7-114">指定發行為服務認證的權杖。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bfa7-115">備註</span><span class="sxs-lookup"><span data-stu-id="8bfa7-115">Remarks</span></span>  
 <span data-ttu-id="8bfa7-116">您應該在利用會發行 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全性權杖之安全權杖服務 (Security Token Service，STS) 的聯合應用程式中使用這個集合。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-116">You should use this collection in a federated application that utilizes a security token service (STS) that issues <xref:System.IdentityModel.Tokens.SamlSecurityToken> security tokens.</span></span> <span data-ttu-id="8bfa7-117">當 STS 發出安全性權杖時，它可以將 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> 加入至安全性權杖中，以便指定此安全性權杖適用之 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-117">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> to the security token.</span></span> <span data-ttu-id="8bfa7-118">如此便可讓接收端 Web 服務的 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 驗證發出的安全性權杖是否適用於此 Web 服務，而驗證的方法則是指定這項檢查應該透過執行下列動作來進行：</span><span class="sxs-lookup"><span data-stu-id="8bfa7-118">That allows the <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="8bfa7-119">將 `audienceUriMode` 的 `<issuedTokenAuthentication>` 屬性設定為 <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> 或 <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-119">Set the `audienceUriMode` attribute of `<issuedTokenAuthentication>` to <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> or <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.</span></span>  
  
- <span data-ttu-id="8bfa7-120">將 URI 加入此集合，以指定有效的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-120">Specify the set of valid URIs, by adding the URIs to this collection.</span></span>  
  
 <span data-ttu-id="8bfa7-121">如需詳細資訊，請參閱 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-121">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="8bfa7-122">如需使用此設定元素的詳細資訊，請參閱[如何：在同盟服務上設定認證](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfa7-122">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bfa7-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bfa7-123">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [<span data-ttu-id="8bfa7-124">安全性行為</span><span class="sxs-lookup"><span data-stu-id="8bfa7-124">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8bfa7-125">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="8bfa7-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8bfa7-126">HOW TO：設定聯合服務的認證</span><span class="sxs-lookup"><span data-stu-id="8bfa7-126">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
