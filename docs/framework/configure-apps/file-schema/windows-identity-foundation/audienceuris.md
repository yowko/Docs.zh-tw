---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941949"
---
# <a name="audienceuris"></a><span data-ttu-id="df44c-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="df44c-101">\<audienceUris></span></span>
<span data-ttu-id="df44c-102">指定 Uri 的集合, 這是信賴憑證者 (RP) 可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="df44c-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="df44c-103">除非權杖的範圍是其中一個允許的物件 Uri, 否則將不會接受。</span><span class="sxs-lookup"><span data-stu-id="df44c-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="df44c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="df44c-104">\<system.identityModel></span></span>  
<span data-ttu-id="df44c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="df44c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="df44c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="df44c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="df44c-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="df44c-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="df44c-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="df44c-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df44c-109">語法</span><span class="sxs-lookup"><span data-stu-id="df44c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df44c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="df44c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="df44c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="df44c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df44c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="df44c-112">Attributes</span></span>  
  
|<span data-ttu-id="df44c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="df44c-113">Attribute</span></span>|<span data-ttu-id="df44c-114">說明</span><span class="sxs-lookup"><span data-stu-id="df44c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df44c-115">模式</span><span class="sxs-lookup"><span data-stu-id="df44c-115">mode</span></span>|<span data-ttu-id="df44c-116"><xref:System.IdentityModel.Selectors.AudienceUriMode>值, 指定物件限制是否應套用至傳入的權杖。</span><span class="sxs-lookup"><span data-stu-id="df44c-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="df44c-117">可能的值為「永遠」、「永不」和「BearerKeyOnly」。</span><span class="sxs-lookup"><span data-stu-id="df44c-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="df44c-118">預設值為「一律」。</span><span class="sxs-lookup"><span data-stu-id="df44c-118">The default is "Always".</span></span> <span data-ttu-id="df44c-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df44c-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df44c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="df44c-120">Child Elements</span></span>  
  
|<span data-ttu-id="df44c-121">項目</span><span class="sxs-lookup"><span data-stu-id="df44c-121">Element</span></span>|<span data-ttu-id="df44c-122">描述</span><span class="sxs-lookup"><span data-stu-id="df44c-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="df44c-123">將`value`屬性所指定的 URI 新增至 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="df44c-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="df44c-124">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="df44c-124">The `value` attribute is required.</span></span> <span data-ttu-id="df44c-125">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="df44c-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="df44c-126">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="df44c-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="df44c-127">所有識別碼都會從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="df44c-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="df44c-128">從 audienceUris 集合中移除`value`屬性所指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="df44c-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="df44c-129">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="df44c-129">The `value` attribute is required.</span></span> <span data-ttu-id="df44c-130">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="df44c-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df44c-131">父項目</span><span class="sxs-lookup"><span data-stu-id="df44c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="df44c-132">項目</span><span class="sxs-lookup"><span data-stu-id="df44c-132">Element</span></span>|<span data-ttu-id="df44c-133">描述</span><span class="sxs-lookup"><span data-stu-id="df44c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df44c-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="df44c-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="df44c-135">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="df44c-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df44c-136">備註</span><span class="sxs-lookup"><span data-stu-id="df44c-136">Remarks</span></span>  
 <span data-ttu-id="df44c-137">根據預設, 集合是空的;使用`<add>`、 `<clear>`和`<remove>`元素來修改集合。</span><span class="sxs-lookup"><span data-stu-id="df44c-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="df44c-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件會使用物件 uri 集合中的值, 來設定物件中任何允許的<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>觀眾 uri 限制。</span><span class="sxs-lookup"><span data-stu-id="df44c-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="df44c-139">`<audienceUris>`元素是<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="df44c-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="df44c-140">新增至集合的個別 URI 會以<xref:System.IdentityModel.Configuration.AudienceUriElement>類別表示。</span><span class="sxs-lookup"><span data-stu-id="df44c-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df44c-141">使用`<audienceUris>`元素做為[ \<identityConfiguration >](identityconfiguration.md)元素的子專案已被取代, 但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="df44c-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="df44c-142">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="df44c-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df44c-143">範例</span><span class="sxs-lookup"><span data-stu-id="df44c-143">Example</span></span>  
 <span data-ttu-id="df44c-144">下列 XML 顯示如何為應用程式設定可接受的物件 Uri。</span><span class="sxs-lookup"><span data-stu-id="df44c-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="df44c-145">這個範例會設定單一 URI。</span><span class="sxs-lookup"><span data-stu-id="df44c-145">This example configures a single URI.</span></span> <span data-ttu-id="df44c-146">將會接受此 URI 範圍內的權杖, 其他所有專案則會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="df44c-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
