---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252010"
---
# <a name="customcookiehandler"></a><span data-ttu-id="acd2d-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="acd2d-101">\<customCookieHandler></span></span>
<span data-ttu-id="acd2d-102">設定自訂 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="acd2d-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="acd2d-103">只有當`mode` `<cookieHandler>`元素的屬性是 "Custom" 時，才會出現此元素。</span><span class="sxs-lookup"><span data-stu-id="acd2d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="acd2d-104">自訂類型必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。</span><span class="sxs-lookup"><span data-stu-id="acd2d-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="acd2d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="acd2d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="acd2d-106">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="acd2d-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="acd2d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="acd2d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="acd2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="acd2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="acd2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="acd2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acd2d-110">語法</span><span class="sxs-lookup"><span data-stu-id="acd2d-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acd2d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="acd2d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="acd2d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="acd2d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acd2d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="acd2d-113">Attributes</span></span>  
  
|<span data-ttu-id="acd2d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="acd2d-114">Attribute</span></span>|<span data-ttu-id="acd2d-115">描述</span><span class="sxs-lookup"><span data-stu-id="acd2d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acd2d-116">型別</span><span class="sxs-lookup"><span data-stu-id="acd2d-116">type</span></span>|<span data-ttu-id="acd2d-117">指定衍生<xref:System.IdentityModel.Services.CookieHandler>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="acd2d-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="acd2d-118">如需如何指定屬性的`type`詳細資訊，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="acd2d-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acd2d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="acd2d-119">Child Elements</span></span>  
 <span data-ttu-id="acd2d-120">None</span><span class="sxs-lookup"><span data-stu-id="acd2d-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acd2d-121">父項目</span><span class="sxs-lookup"><span data-stu-id="acd2d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="acd2d-122">項目</span><span class="sxs-lookup"><span data-stu-id="acd2d-122">Element</span></span>|<span data-ttu-id="acd2d-123">描述</span><span class="sxs-lookup"><span data-stu-id="acd2d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acd2d-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="acd2d-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="acd2d-125"><xref:System.IdentityModel.Services.CookieHandler> 設定用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="acd2d-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acd2d-126">備註</span><span class="sxs-lookup"><span data-stu-id="acd2d-126">Remarks</span></span>  
 <span data-ttu-id="acd2d-127">當您藉由將專案的`mode`屬性`<cookieHandler>`設定為 "custom" 來指定自訂 cookie 處理常式時，您必須包含參考 cookie 處理常式類型的`<customCookieHandler>`子項目，以指定自訂 cookie 處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="acd2d-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="acd2d-128">當屬性設定為 "分塊" `mode`或 "Default" 時，無法指定此元素。</span><span class="sxs-lookup"><span data-stu-id="acd2d-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="acd2d-129">自訂 cookie 處理常式必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。</span><span class="sxs-lookup"><span data-stu-id="acd2d-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="acd2d-130">`<customCookieHandler>`元素是<xref:System.IdentityModel.Configuration.CustomTypeElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="acd2d-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acd2d-131">範例</span><span class="sxs-lookup"><span data-stu-id="acd2d-131">Example</span></span>  
 <span data-ttu-id="acd2d-132">下列範例會將 SAM 設定為使用類型`MyNamespace.MyCustomCookieHandler`的自訂 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="acd2d-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="acd2d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd2d-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
