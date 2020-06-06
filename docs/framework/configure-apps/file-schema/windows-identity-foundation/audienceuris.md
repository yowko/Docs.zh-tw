---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252175"
---
# \<audienceUris>
<span data-ttu-id="9cf12-101">指定 Uri 的集合，這是信賴憑證者（RP）可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cf12-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="9cf12-102">除非權杖屬於其中一個允許的 Audience URI，否則不接受這些權杖。</span><span class="sxs-lookup"><span data-stu-id="9cf12-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="9cf12-103">語法</span><span class="sxs-lookup"><span data-stu-id="9cf12-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cf12-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9cf12-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9cf12-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9cf12-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cf12-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9cf12-106">Attributes</span></span>  
  
|<span data-ttu-id="9cf12-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9cf12-107">Attribute</span></span>|<span data-ttu-id="9cf12-108">描述</span><span class="sxs-lookup"><span data-stu-id="9cf12-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cf12-109">mode</span><span class="sxs-lookup"><span data-stu-id="9cf12-109">mode</span></span>|<span data-ttu-id="9cf12-110"><xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定物件限制是否應套用至傳入的權杖。</span><span class="sxs-lookup"><span data-stu-id="9cf12-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="9cf12-111">可能的值為「永遠」、「永不」和「BearerKeyOnly」。</span><span class="sxs-lookup"><span data-stu-id="9cf12-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="9cf12-112">預設值為「一律」。</span><span class="sxs-lookup"><span data-stu-id="9cf12-112">The default is "Always".</span></span> <span data-ttu-id="9cf12-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9cf12-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cf12-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9cf12-114">Child Elements</span></span>  
  
|<span data-ttu-id="9cf12-115">元素</span><span class="sxs-lookup"><span data-stu-id="9cf12-115">Element</span></span>|<span data-ttu-id="9cf12-116">描述</span><span class="sxs-lookup"><span data-stu-id="9cf12-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="9cf12-117">將屬性所指定的 URI 新增 `value` 至 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="9cf12-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="9cf12-118">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="9cf12-118">The `value` attribute is required.</span></span> <span data-ttu-id="9cf12-119">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9cf12-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="9cf12-120">清除 audienceUris 集合。</span><span class="sxs-lookup"><span data-stu-id="9cf12-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="9cf12-121">所有識別碼都會從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="9cf12-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="9cf12-122">`value`從 audienceUris 集合中移除屬性所指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="9cf12-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="9cf12-123">`value` 屬性 (Attribute) 是必要項。</span><span class="sxs-lookup"><span data-stu-id="9cf12-123">The `value` attribute is required.</span></span> <span data-ttu-id="9cf12-124">URI 會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9cf12-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9cf12-125">父項目</span><span class="sxs-lookup"><span data-stu-id="9cf12-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9cf12-126">元素</span><span class="sxs-lookup"><span data-stu-id="9cf12-126">Element</span></span>|<span data-ttu-id="9cf12-127">描述</span><span class="sxs-lookup"><span data-stu-id="9cf12-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9cf12-128">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="9cf12-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cf12-129">備註</span><span class="sxs-lookup"><span data-stu-id="9cf12-129">Remarks</span></span>  
 <span data-ttu-id="9cf12-130">根據預設，集合是空的;使用 `<add>` 、 `<clear>` 和 `<remove>` 元素來修改集合。</span><span class="sxs-lookup"><span data-stu-id="9cf12-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="9cf12-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>和 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 物件會使用物件 uri 集合中的值，來設定物件中任何允許的觀眾 uri 限制 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="9cf12-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="9cf12-132">`<audienceUris>`元素是由 <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="9cf12-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="9cf12-133">新增至集合的個別 URI 會以 <xref:System.IdentityModel.Configuration.AudienceUriElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="9cf12-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cf12-134">使用專案 `<audienceUris>` 做為專案的子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9cf12-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9cf12-135">元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="9cf12-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cf12-136">範例</span><span class="sxs-lookup"><span data-stu-id="9cf12-136">Example</span></span>  
 <span data-ttu-id="9cf12-137">下列 XML 顯示如何為應用程式設定可接受的物件 Uri。</span><span class="sxs-lookup"><span data-stu-id="9cf12-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="9cf12-138">這個範例會設定單一 URI。</span><span class="sxs-lookup"><span data-stu-id="9cf12-138">This example configures a single URI.</span></span> <span data-ttu-id="9cf12-139">將會接受此 URI 範圍內的權杖，其他所有專案則會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="9cf12-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
