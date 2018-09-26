---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216642"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="b2a70-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="b2a70-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="b2a70-103">指定是可接受的識別項的信賴憑證者的合作對象 (RP) 的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="b2a70-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="b2a70-104">除非其中一個允許的對象 Uri 的範圍，將不會接受權杖。</span><span class="sxs-lookup"><span data-stu-id="b2a70-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="b2a70-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b2a70-105">\<system.identityModel></span></span>  
<span data-ttu-id="b2a70-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b2a70-106">\<identityConfiguration></span></span>  
<span data-ttu-id="b2a70-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="b2a70-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b2a70-108">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="b2a70-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="b2a70-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="b2a70-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a70-110">語法</span><span class="sxs-lookup"><span data-stu-id="b2a70-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2a70-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b2a70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2a70-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b2a70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2a70-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b2a70-113">Attributes</span></span>  
  
|<span data-ttu-id="b2a70-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b2a70-114">Attribute</span></span>|<span data-ttu-id="b2a70-115">描述</span><span class="sxs-lookup"><span data-stu-id="b2a70-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2a70-116">模式</span><span class="sxs-lookup"><span data-stu-id="b2a70-116">mode</span></span>|<span data-ttu-id="b2a70-117"><xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應該套用對象限制連入的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b2a70-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="b2a70-118">可能的值為 「 永遠 」，「 從未 」，和 「 BearerKeyOnly"。</span><span class="sxs-lookup"><span data-stu-id="b2a70-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="b2a70-119">預設值為 [一律]。</span><span class="sxs-lookup"><span data-stu-id="b2a70-119">The default is "Always".</span></span> <span data-ttu-id="b2a70-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b2a70-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2a70-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b2a70-121">Child Elements</span></span>  
  
|<span data-ttu-id="b2a70-122">項目</span><span class="sxs-lookup"><span data-stu-id="b2a70-122">Element</span></span>|<span data-ttu-id="b2a70-123">描述</span><span class="sxs-lookup"><span data-stu-id="b2a70-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="b2a70-124">將所指定的 URI `value` audienceUris 集合屬性。</span><span class="sxs-lookup"><span data-stu-id="b2a70-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="b2a70-125">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="b2a70-125">The `value` attribute is required.</span></span> <span data-ttu-id="b2a70-126">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b2a70-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="b2a70-127">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="b2a70-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="b2a70-128">從集合移除所有的識別項。</span><span class="sxs-lookup"><span data-stu-id="b2a70-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="b2a70-129">移除所指定的 URI `value` audienceUris 集合中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2a70-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="b2a70-130">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="b2a70-130">The `value` attribute is required.</span></span> <span data-ttu-id="b2a70-131">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b2a70-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2a70-132">父項目</span><span class="sxs-lookup"><span data-stu-id="b2a70-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b2a70-133">項目</span><span class="sxs-lookup"><span data-stu-id="b2a70-133">Element</span></span>|<span data-ttu-id="b2a70-134">描述</span><span class="sxs-lookup"><span data-stu-id="b2a70-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2a70-135">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="b2a70-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b2a70-136">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="b2a70-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2a70-137">備註</span><span class="sxs-lookup"><span data-stu-id="b2a70-137">Remarks</span></span>  
 <span data-ttu-id="b2a70-138">根據預設，集合是空的。使用  `<add>`， `<clear>`，和`<remove>`來修改集合的項目。</span><span class="sxs-lookup"><span data-stu-id="b2a70-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="b2a70-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 並<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件中設定任何的對象 URI 集合的值允許的對象 URI 限制的使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。</span><span class="sxs-lookup"><span data-stu-id="b2a70-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="b2a70-140">`<audienceUris>`項目由<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="b2a70-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="b2a70-141">加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。</span><span class="sxs-lookup"><span data-stu-id="b2a70-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2a70-142">善用`<audienceUris>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="b2a70-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b2a70-143">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="b2a70-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2a70-144">範例</span><span class="sxs-lookup"><span data-stu-id="b2a70-144">Example</span></span>  
 <span data-ttu-id="b2a70-145">下列 XML 示範如何設定應用程式的可接受對象 Uri。</span><span class="sxs-lookup"><span data-stu-id="b2a70-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="b2a70-146">這個範例會設定一個單一的 URI。</span><span class="sxs-lookup"><span data-stu-id="b2a70-146">This example configures a single URI.</span></span> <span data-ttu-id="b2a70-147">這個 uri 範圍的權杖會被接受，其他所有人將會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="b2a70-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
