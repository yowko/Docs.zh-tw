---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942789"
---
# <a name="customcookiehandler"></a><span data-ttu-id="5ab7f-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="5ab7f-101">\<customCookieHandler></span></span>
<span data-ttu-id="5ab7f-102">設定自訂 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="5ab7f-103">只有當`mode` `<cookieHandler>`元素的屬性是 "Custom" 時, 才會出現此元素。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="5ab7f-104">自訂類型必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="5ab7f-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="5ab7f-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="5ab7f-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="5ab7f-106">\<federationConfiguration></span></span>  
<span data-ttu-id="5ab7f-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="5ab7f-107">\<cookieHandler></span></span>  
<span data-ttu-id="5ab7f-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="5ab7f-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab7f-109">語法</span><span class="sxs-lookup"><span data-stu-id="5ab7f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ab7f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ab7f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ab7f-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ab7f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5ab7f-112">Attributes</span></span>  
  
|<span data-ttu-id="5ab7f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5ab7f-113">Attribute</span></span>|<span data-ttu-id="5ab7f-114">描述</span><span class="sxs-lookup"><span data-stu-id="5ab7f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ab7f-115">型別</span><span class="sxs-lookup"><span data-stu-id="5ab7f-115">type</span></span>|<span data-ttu-id="5ab7f-116">指定衍生<xref:System.IdentityModel.Services.CookieHandler>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="5ab7f-117">如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ab7f-118">子元素</span><span class="sxs-lookup"><span data-stu-id="5ab7f-118">Child Elements</span></span>  
 <span data-ttu-id="5ab7f-119">無</span><span class="sxs-lookup"><span data-stu-id="5ab7f-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ab7f-120">父項目</span><span class="sxs-lookup"><span data-stu-id="5ab7f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5ab7f-121">項目</span><span class="sxs-lookup"><span data-stu-id="5ab7f-121">Element</span></span>|<span data-ttu-id="5ab7f-122">描述</span><span class="sxs-lookup"><span data-stu-id="5ab7f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ab7f-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="5ab7f-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="5ab7f-124"><xref:System.IdentityModel.Services.CookieHandler> 設定用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab7f-125">備註</span><span class="sxs-lookup"><span data-stu-id="5ab7f-125">Remarks</span></span>  
 <span data-ttu-id="5ab7f-126">當您藉由將專案的`mode`屬性`<cookieHandler>`設定為 "custom" 來指定自訂 cookie 處理常式時, 您必須包含參考 cookie 處理常式類型的`<customCookieHandler>`子項目, 以指定自訂 cookie 處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="5ab7f-127">當屬性設定為 "分塊" `mode`或 "Default" 時, 無法指定此元素。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="5ab7f-128">自訂 cookie 處理常式必須衍生<xref:System.IdentityModel.Services.CookieHandler>自類別。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="5ab7f-129">`<customCookieHandler>`元素是<xref:System.IdentityModel.Configuration.CustomTypeElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ab7f-130">範例</span><span class="sxs-lookup"><span data-stu-id="5ab7f-130">Example</span></span>  
 <span data-ttu-id="5ab7f-131">下列範例會將 SAM 設定為使用類型`MyNamespace.MyCustomCookieHandler`的自訂 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="5ab7f-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ab7f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab7f-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
