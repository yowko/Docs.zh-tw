---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791725"
---
# <a name="customcookiehandler"></a><span data-ttu-id="b7dce-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="b7dce-101">\<customCookieHandler></span></span>
<span data-ttu-id="b7dce-102">設定自訂 cookie 處理常式型別。</span><span class="sxs-lookup"><span data-stu-id="b7dce-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="b7dce-103">這個項目只會出現如果`mode`屬性的`<cookieHandler>`項目是 「 自訂 」。</span><span class="sxs-lookup"><span data-stu-id="b7dce-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="b7dce-104">自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="b7dce-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="b7dce-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="b7dce-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="b7dce-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="b7dce-106">\<federationConfiguration></span></span>  
<span data-ttu-id="b7dce-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="b7dce-107">\<cookieHandler></span></span>  
<span data-ttu-id="b7dce-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="b7dce-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dce-109">語法</span><span class="sxs-lookup"><span data-stu-id="b7dce-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7dce-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b7dce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7dce-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b7dce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7dce-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b7dce-112">Attributes</span></span>  
  
|<span data-ttu-id="b7dce-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b7dce-113">Attribute</span></span>|<span data-ttu-id="b7dce-114">描述</span><span class="sxs-lookup"><span data-stu-id="b7dce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7dce-115">類型</span><span class="sxs-lookup"><span data-stu-id="b7dce-115">type</span></span>|<span data-ttu-id="b7dce-116">指定自訂型別衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="b7dce-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="b7dce-117">如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b7dce-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7dce-118">子元素</span><span class="sxs-lookup"><span data-stu-id="b7dce-118">Child Elements</span></span>  
 <span data-ttu-id="b7dce-119">None</span><span class="sxs-lookup"><span data-stu-id="b7dce-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7dce-120">父項目</span><span class="sxs-lookup"><span data-stu-id="b7dce-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b7dce-121">項目</span><span class="sxs-lookup"><span data-stu-id="b7dce-121">Element</span></span>|<span data-ttu-id="b7dce-122">描述</span><span class="sxs-lookup"><span data-stu-id="b7dce-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7dce-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="b7dce-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="b7dce-124">會設定<xref:System.IdentityModel.Services.CookieHandler>，<xref:System.IdentityModel.Services.SessionAuthenticationModule>用以讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="b7dce-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7dce-125">備註</span><span class="sxs-lookup"><span data-stu-id="b7dce-125">Remarks</span></span>  
 <span data-ttu-id="b7dce-126">當您設定以指定自訂 cookie 處理常式`mode`的屬性`<cookieHandler>`項目為"Custom"，您必須指定自訂 cookie 處理常式的類型包括`<customCookieHandler>`子項目會參考的 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="b7dce-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="b7dce-127">此元素不能指定何時`mode`屬性設為"Chunked"或"Default"。</span><span class="sxs-lookup"><span data-stu-id="b7dce-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="b7dce-128">自訂 cookie 處理常式必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="b7dce-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="b7dce-129">`<customCookieHandler>`項目由<xref:System.IdentityModel.Configuration.CustomTypeElement>類別。</span><span class="sxs-lookup"><span data-stu-id="b7dce-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7dce-130">範例</span><span class="sxs-lookup"><span data-stu-id="b7dce-130">Example</span></span>  
 <span data-ttu-id="b7dce-131">下列範例會設定使用自訂的 cookie 處理常式類型的 SAM `MyNamespace.MyCustomCookieHandler`。</span><span class="sxs-lookup"><span data-stu-id="b7dce-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7dce-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7dce-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
