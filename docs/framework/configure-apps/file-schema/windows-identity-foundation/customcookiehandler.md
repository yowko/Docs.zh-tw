---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="a6aa4-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="a6aa4-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="a6aa4-103">設定自訂的 cookie 處理常式型別。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="a6aa4-104">這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`項目是 「 自訂 」。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="a6aa4-105">自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="a6aa4-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="a6aa4-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="a6aa4-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a6aa4-107">\<federationConfiguration></span></span>  
<span data-ttu-id="a6aa4-108">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="a6aa4-108">\<cookieHandler></span></span>  
<span data-ttu-id="a6aa4-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="a6aa4-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6aa4-110">語法</span><span class="sxs-lookup"><span data-stu-id="a6aa4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6aa4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6aa4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6aa4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6aa4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a6aa4-113">Attributes</span></span>  
  
|<span data-ttu-id="a6aa4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a6aa4-114">Attribute</span></span>|<span data-ttu-id="a6aa4-115">描述</span><span class="sxs-lookup"><span data-stu-id="a6aa4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6aa4-116">類型</span><span class="sxs-lookup"><span data-stu-id="a6aa4-116">type</span></span>|<span data-ttu-id="a6aa4-117">指定自訂型別衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="a6aa4-118">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6aa4-119">子項目</span><span class="sxs-lookup"><span data-stu-id="a6aa4-119">Child Elements</span></span>  
 <span data-ttu-id="a6aa4-120">無</span><span class="sxs-lookup"><span data-stu-id="a6aa4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6aa4-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a6aa4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a6aa4-122">項目</span><span class="sxs-lookup"><span data-stu-id="a6aa4-122">Element</span></span>|<span data-ttu-id="a6aa4-123">描述</span><span class="sxs-lookup"><span data-stu-id="a6aa4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6aa4-124">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="a6aa4-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="a6aa4-125">設定<xref:System.IdentityModel.Services.CookieHandler>，<xref:System.IdentityModel.Services.SessionAuthenticationModule>用來讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6aa4-126">備註</span><span class="sxs-lookup"><span data-stu-id="a6aa4-126">Remarks</span></span>  
 <span data-ttu-id="a6aa4-127">當您指定自訂 cookie 處理常式設定`mode`屬性`<cookieHandler>`項目為"Custom"，您必須指定自訂 cookie 處理常式的類型包括`<customCookieHandler>`參考 cookie 處理常式類型的子元素。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="a6aa4-128">此元素不能指定何時`mode`屬性設為"Chunked"或"Default"。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="a6aa4-129">自訂的 cookie 處理常式必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="a6aa4-130">`<customCookieHandler>`項目由<xref:System.IdentityModel.Configuration.CustomTypeElement>類別。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6aa4-131">範例</span><span class="sxs-lookup"><span data-stu-id="a6aa4-131">Example</span></span>  
 <span data-ttu-id="a6aa4-132">下列範例會設定使用自訂的 cookie 處理常式類型的 SAM `MyNamespace.MyCustomCookieHandler`。</span><span class="sxs-lookup"><span data-stu-id="a6aa4-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6aa4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6aa4-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
