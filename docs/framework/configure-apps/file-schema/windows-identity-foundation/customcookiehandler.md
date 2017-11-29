---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: df95e8d47d6a19e4fd488fa14bc771bc2c2b56b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="52f01-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="52f01-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="52f01-103">設定自訂的 cookie 處理常式型別。</span><span class="sxs-lookup"><span data-stu-id="52f01-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="52f01-104">這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`項目是 「 自訂 」。</span><span class="sxs-lookup"><span data-stu-id="52f01-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="52f01-105">自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="52f01-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="52f01-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="52f01-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="52f01-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="52f01-107">\<federationConfiguration></span></span>  
<span data-ttu-id="52f01-108">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="52f01-108">\<cookieHandler></span></span>  
<span data-ttu-id="52f01-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="52f01-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f01-110">語法</span><span class="sxs-lookup"><span data-stu-id="52f01-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52f01-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="52f01-111">Attributes and Elements</span></span>  
 <span data-ttu-id="52f01-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="52f01-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52f01-113">屬性</span><span class="sxs-lookup"><span data-stu-id="52f01-113">Attributes</span></span>  
  
|<span data-ttu-id="52f01-114">屬性</span><span class="sxs-lookup"><span data-stu-id="52f01-114">Attribute</span></span>|<span data-ttu-id="52f01-115">描述</span><span class="sxs-lookup"><span data-stu-id="52f01-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52f01-116">類型</span><span class="sxs-lookup"><span data-stu-id="52f01-116">type</span></span>|<span data-ttu-id="52f01-117">指定自訂型別衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="52f01-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="52f01-118">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52f01-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52f01-119">子元素</span><span class="sxs-lookup"><span data-stu-id="52f01-119">Child Elements</span></span>  
 <span data-ttu-id="52f01-120">無</span><span class="sxs-lookup"><span data-stu-id="52f01-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52f01-121">父項目</span><span class="sxs-lookup"><span data-stu-id="52f01-121">Parent Elements</span></span>  
  
|<span data-ttu-id="52f01-122">項目</span><span class="sxs-lookup"><span data-stu-id="52f01-122">Element</span></span>|<span data-ttu-id="52f01-123">說明</span><span class="sxs-lookup"><span data-stu-id="52f01-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52f01-124">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="52f01-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="52f01-125">設定<xref:System.IdentityModel.Services.CookieHandler>，<xref:System.IdentityModel.Services.SessionAuthenticationModule>用來讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="52f01-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52f01-126">備註</span><span class="sxs-lookup"><span data-stu-id="52f01-126">Remarks</span></span>  
 <span data-ttu-id="52f01-127">當您指定自訂 cookie 處理常式設定`mode`屬性`<cookieHandler>`項目為"Custom"，您必須指定自訂 cookie 處理常式的類型包括`<customCookieHandler>`參考 cookie 處理常式類型的子元素。</span><span class="sxs-lookup"><span data-stu-id="52f01-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="52f01-128">此元素不能指定何時`mode`屬性設為"Chunked"或"Default"。</span><span class="sxs-lookup"><span data-stu-id="52f01-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="52f01-129">自訂的 cookie 處理常式必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="52f01-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="52f01-130">`<customCookieHandler>`項目由<xref:System.IdentityModel.Configuration.CustomTypeElement>類別。</span><span class="sxs-lookup"><span data-stu-id="52f01-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52f01-131">範例</span><span class="sxs-lookup"><span data-stu-id="52f01-131">Example</span></span>  
 <span data-ttu-id="52f01-132">下列範例會設定使用自訂的 cookie 處理常式類型的 SAM `MyNamespace.MyCustomCookieHandler`。</span><span class="sxs-lookup"><span data-stu-id="52f01-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52f01-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52f01-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
