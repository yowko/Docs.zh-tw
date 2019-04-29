---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750744"
---
# <a name="audienceuris"></a><span data-ttu-id="e433d-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="e433d-101">\<audienceUris></span></span>
<span data-ttu-id="e433d-102">指定是可接受的識別項的信賴憑證者的合作對象 (RP) 的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="e433d-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="e433d-103">除非其中一個允許的對象 Uri 的範圍，將不會接受權杖。</span><span class="sxs-lookup"><span data-stu-id="e433d-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="e433d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e433d-104">\<system.identityModel></span></span>  
<span data-ttu-id="e433d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e433d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e433d-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e433d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e433d-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e433d-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e433d-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="e433d-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e433d-109">語法</span><span class="sxs-lookup"><span data-stu-id="e433d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e433d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e433d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e433d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e433d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e433d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e433d-112">Attributes</span></span>  
  
|<span data-ttu-id="e433d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e433d-113">Attribute</span></span>|<span data-ttu-id="e433d-114">描述</span><span class="sxs-lookup"><span data-stu-id="e433d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e433d-115">模式</span><span class="sxs-lookup"><span data-stu-id="e433d-115">mode</span></span>|<span data-ttu-id="e433d-116"><xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應該套用對象限制連入的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e433d-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="e433d-117">可能的值為 「 永遠 」，「 從未 」，和 「 BearerKeyOnly"。</span><span class="sxs-lookup"><span data-stu-id="e433d-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="e433d-118">預設值為 [一律]。</span><span class="sxs-lookup"><span data-stu-id="e433d-118">The default is "Always".</span></span> <span data-ttu-id="e433d-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e433d-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e433d-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e433d-120">Child Elements</span></span>  
  
|<span data-ttu-id="e433d-121">項目</span><span class="sxs-lookup"><span data-stu-id="e433d-121">Element</span></span>|<span data-ttu-id="e433d-122">描述</span><span class="sxs-lookup"><span data-stu-id="e433d-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="e433d-123">將所指定的 URI `value` audienceUris 集合屬性。</span><span class="sxs-lookup"><span data-stu-id="e433d-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="e433d-124">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="e433d-124">The `value` attribute is required.</span></span> <span data-ttu-id="e433d-125">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e433d-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="e433d-126">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="e433d-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="e433d-127">從集合移除所有的識別項。</span><span class="sxs-lookup"><span data-stu-id="e433d-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="e433d-128">移除所指定的 URI `value` audienceUris 集合中的屬性。</span><span class="sxs-lookup"><span data-stu-id="e433d-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="e433d-129">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="e433d-129">The `value` attribute is required.</span></span> <span data-ttu-id="e433d-130">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e433d-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e433d-131">父項目</span><span class="sxs-lookup"><span data-stu-id="e433d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e433d-132">項目</span><span class="sxs-lookup"><span data-stu-id="e433d-132">Element</span></span>|<span data-ttu-id="e433d-133">描述</span><span class="sxs-lookup"><span data-stu-id="e433d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e433d-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e433d-134">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e433d-135">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="e433d-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e433d-136">備註</span><span class="sxs-lookup"><span data-stu-id="e433d-136">Remarks</span></span>  
 <span data-ttu-id="e433d-137">根據預設，集合是空的。使用  `<add>`， `<clear>`，和`<remove>`來修改集合的項目。</span><span class="sxs-lookup"><span data-stu-id="e433d-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="e433d-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 並<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件中設定任何的對象 URI 集合的值允許的對象 URI 限制的使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。</span><span class="sxs-lookup"><span data-stu-id="e433d-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="e433d-139">`<audienceUris>`項目由<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="e433d-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="e433d-140">加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。</span><span class="sxs-lookup"><span data-stu-id="e433d-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e433d-141">善用`<audienceUris>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="e433d-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e433d-142">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="e433d-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e433d-143">範例</span><span class="sxs-lookup"><span data-stu-id="e433d-143">Example</span></span>  
 <span data-ttu-id="e433d-144">下列 XML 示範如何設定應用程式的可接受對象 Uri。</span><span class="sxs-lookup"><span data-stu-id="e433d-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="e433d-145">這個範例會設定一個單一的 URI。</span><span class="sxs-lookup"><span data-stu-id="e433d-145">This example configures a single URI.</span></span> <span data-ttu-id="e433d-146">這個 uri 範圍的權杖會被接受，其他所有人將會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="e433d-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
