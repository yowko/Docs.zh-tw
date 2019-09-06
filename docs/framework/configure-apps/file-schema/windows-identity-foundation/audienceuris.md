---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252175"
---
# <a name="audienceuris"></a><span data-ttu-id="f45d3-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="f45d3-101">\<audienceUris></span></span>
<span data-ttu-id="f45d3-102">指定 Uri 的集合，這是信賴憑證者（RP）可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f45d3-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="f45d3-103">除非權杖的範圍是其中一個允許的物件 Uri，否則將不會接受。</span><span class="sxs-lookup"><span data-stu-id="f45d3-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
<span data-ttu-id="f45d3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f45d3-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f45d3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f45d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f45d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f45d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="f45d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**</span><span class="sxs-lookup"><span data-stu-id="f45d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f45d3-110">語法</span><span class="sxs-lookup"><span data-stu-id="f45d3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f45d3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f45d3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f45d3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f45d3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f45d3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f45d3-113">Attributes</span></span>  
  
|<span data-ttu-id="f45d3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f45d3-114">Attribute</span></span>|<span data-ttu-id="f45d3-115">描述</span><span class="sxs-lookup"><span data-stu-id="f45d3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f45d3-116">模式</span><span class="sxs-lookup"><span data-stu-id="f45d3-116">mode</span></span>|<span data-ttu-id="f45d3-117"><xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定物件限制是否應套用至傳入的權杖。</span><span class="sxs-lookup"><span data-stu-id="f45d3-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="f45d3-118">可能的值為「永遠」、「永不」和「BearerKeyOnly」。</span><span class="sxs-lookup"><span data-stu-id="f45d3-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="f45d3-119">預設值為「一律」。</span><span class="sxs-lookup"><span data-stu-id="f45d3-119">The default is "Always".</span></span> <span data-ttu-id="f45d3-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f45d3-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f45d3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="f45d3-121">Child Elements</span></span>  
  
|<span data-ttu-id="f45d3-122">項目</span><span class="sxs-lookup"><span data-stu-id="f45d3-122">Element</span></span>|<span data-ttu-id="f45d3-123">描述</span><span class="sxs-lookup"><span data-stu-id="f45d3-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="f45d3-124">將`value`屬性所指定的 URI 新增至 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="f45d3-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="f45d3-125">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="f45d3-125">The `value` attribute is required.</span></span> <span data-ttu-id="f45d3-126">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f45d3-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="f45d3-127">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="f45d3-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="f45d3-128">所有識別碼都會從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="f45d3-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="f45d3-129">從 audienceUris 集合中移除`value`屬性所指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="f45d3-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="f45d3-130">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="f45d3-130">The `value` attribute is required.</span></span> <span data-ttu-id="f45d3-131">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f45d3-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f45d3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="f45d3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f45d3-133">項目</span><span class="sxs-lookup"><span data-stu-id="f45d3-133">Element</span></span>|<span data-ttu-id="f45d3-134">描述</span><span class="sxs-lookup"><span data-stu-id="f45d3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f45d3-135">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="f45d3-135">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f45d3-136">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="f45d3-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f45d3-137">備註</span><span class="sxs-lookup"><span data-stu-id="f45d3-137">Remarks</span></span>  
 <span data-ttu-id="f45d3-138">根據預設，集合是空的;使用`<add>`、 `<clear>`和`<remove>`元素來修改集合。</span><span class="sxs-lookup"><span data-stu-id="f45d3-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="f45d3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件會使用物件 uri 集合中的值，來設定物件中任何允許的<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>觀眾 uri 限制。</span><span class="sxs-lookup"><span data-stu-id="f45d3-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="f45d3-140">`<audienceUris>`元素是<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="f45d3-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="f45d3-141">新增至集合的個別 URI 會以<xref:System.IdentityModel.Configuration.AudienceUriElement>類別表示。</span><span class="sxs-lookup"><span data-stu-id="f45d3-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f45d3-142">使用`<audienceUris>`元素做為[ \<identityConfiguration >](identityconfiguration.md)元素的子專案已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="f45d3-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="f45d3-143">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="f45d3-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f45d3-144">範例</span><span class="sxs-lookup"><span data-stu-id="f45d3-144">Example</span></span>  
 <span data-ttu-id="f45d3-145">下列 XML 顯示如何為應用程式設定可接受的物件 Uri。</span><span class="sxs-lookup"><span data-stu-id="f45d3-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="f45d3-146">這個範例會設定單一 URI。</span><span class="sxs-lookup"><span data-stu-id="f45d3-146">This example configures a single URI.</span></span> <span data-ttu-id="f45d3-147">將會接受此 URI 範圍內的權杖，其他所有專案則會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="f45d3-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
