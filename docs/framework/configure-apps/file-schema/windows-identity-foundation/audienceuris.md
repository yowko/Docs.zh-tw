---
title: '&lt;audienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 69c96698b309a789b4527c76e1fe8b8b99811a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="1dff3-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="1dff3-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="1dff3-103">指定是可接受的識別項的信賴憑證者的合作對象 (RP) 的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="1dff3-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="1dff3-104">除非它們適用其中一個允許的 audience Uri，將不會接受權杖。</span><span class="sxs-lookup"><span data-stu-id="1dff3-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="1dff3-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1dff3-105">\<system.identityModel></span></span>  
<span data-ttu-id="1dff3-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1dff3-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1dff3-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1dff3-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1dff3-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1dff3-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="1dff3-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="1dff3-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dff3-110">語法</span><span class="sxs-lookup"><span data-stu-id="1dff3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dff3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dff3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1dff3-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1dff3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dff3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1dff3-113">Attributes</span></span>  
  
|<span data-ttu-id="1dff3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1dff3-114">Attribute</span></span>|<span data-ttu-id="1dff3-115">描述</span><span class="sxs-lookup"><span data-stu-id="1dff3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dff3-116">模式</span><span class="sxs-lookup"><span data-stu-id="1dff3-116">mode</span></span>|<span data-ttu-id="1dff3-117"><xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否應該套用對象限制傳入語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1dff3-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="1dff3-118">可能的值為 「 永遠 」、 「 永不 」，和 「 BearerKeyOnly"。</span><span class="sxs-lookup"><span data-stu-id="1dff3-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="1dff3-119">預設為"Always"。</span><span class="sxs-lookup"><span data-stu-id="1dff3-119">The default is "Always".</span></span> <span data-ttu-id="1dff3-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1dff3-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dff3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="1dff3-121">Child Elements</span></span>  
  
|<span data-ttu-id="1dff3-122">項目</span><span class="sxs-lookup"><span data-stu-id="1dff3-122">Element</span></span>|<span data-ttu-id="1dff3-123">描述</span><span class="sxs-lookup"><span data-stu-id="1dff3-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="1dff3-124">加入所指定的 URI `value` audienceUris 集合屬性。</span><span class="sxs-lookup"><span data-stu-id="1dff3-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="1dff3-125">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="1dff3-125">The `value` attribute is required.</span></span> <span data-ttu-id="1dff3-126">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1dff3-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="1dff3-127">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="1dff3-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="1dff3-128">從集合移除所有的識別項。</span><span class="sxs-lookup"><span data-stu-id="1dff3-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="1dff3-129">移除所指定的 URI `value` audienceUris 集合中的屬性。</span><span class="sxs-lookup"><span data-stu-id="1dff3-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="1dff3-130">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="1dff3-130">The `value` attribute is required.</span></span> <span data-ttu-id="1dff3-131">URI 是區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="1dff3-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dff3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="1dff3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="1dff3-133">項目</span><span class="sxs-lookup"><span data-stu-id="1dff3-133">Element</span></span>|<span data-ttu-id="1dff3-134">描述</span><span class="sxs-lookup"><span data-stu-id="1dff3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dff3-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1dff3-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1dff3-136">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="1dff3-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dff3-137">備註</span><span class="sxs-lookup"><span data-stu-id="1dff3-137">Remarks</span></span>  
 <span data-ttu-id="1dff3-138">根據預設，這個集合是空的。使用`<add>`， `<clear>`，和`<remove>`修改該集合的項目。</span><span class="sxs-lookup"><span data-stu-id="1dff3-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="1dff3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件來設定任何的對象 URI 集合中的值允許的 audience URI 限制使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。</span><span class="sxs-lookup"><span data-stu-id="1dff3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="1dff3-140">`<audienceUris>`項目由<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="1dff3-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="1dff3-141">加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。</span><span class="sxs-lookup"><span data-stu-id="1dff3-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dff3-142">使用`<audienceUris>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="1dff3-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="1dff3-143">設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="1dff3-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dff3-144">範例</span><span class="sxs-lookup"><span data-stu-id="1dff3-144">Example</span></span>  
 <span data-ttu-id="1dff3-145">下列 XML 會示範如何設定應用程式可接受的 audience Uri。</span><span class="sxs-lookup"><span data-stu-id="1dff3-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="1dff3-146">這個範例會設定單一的 URI。</span><span class="sxs-lookup"><span data-stu-id="1dff3-146">This example configures a single URI.</span></span> <span data-ttu-id="1dff3-147">此 URI 範圍內的語彙基元會被接受，其他所有項目將會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="1dff3-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
