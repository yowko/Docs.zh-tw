---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a8ee23ac6facaea18cd7f1820616cb9b16afa336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189847"
---
# \<customCookieHandler>

<span data-ttu-id="5c246-101">設定自訂的 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="5c246-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="5c246-102">如果 `mode` 元素的屬性 `<cookieHandler>` 是 "Custom"，則這個元素可能只有存在。</span><span class="sxs-lookup"><span data-stu-id="5c246-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="5c246-103">自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="5c246-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="5c246-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c246-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c246-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5c246-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5c246-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5c246-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c246-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5c246-107">Attributes</span></span>  
  
|<span data-ttu-id="5c246-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5c246-108">Attribute</span></span>|<span data-ttu-id="5c246-109">描述</span><span class="sxs-lookup"><span data-stu-id="5c246-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c246-110">type</span><span class="sxs-lookup"><span data-stu-id="5c246-110">type</span></span>|<span data-ttu-id="5c246-111">指定衍生自類別的自訂型別 <xref:System.IdentityModel.Services.CookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="5c246-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="5c246-112">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5c246-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c246-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5c246-113">Child Elements</span></span>  

 <span data-ttu-id="5c246-114">無</span><span class="sxs-lookup"><span data-stu-id="5c246-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c246-115">父項目</span><span class="sxs-lookup"><span data-stu-id="5c246-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5c246-116">項目</span><span class="sxs-lookup"><span data-stu-id="5c246-116">Element</span></span>|<span data-ttu-id="5c246-117">描述</span><span class="sxs-lookup"><span data-stu-id="5c246-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="5c246-118">設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 用來讀取和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="5c246-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c246-119">備註</span><span class="sxs-lookup"><span data-stu-id="5c246-119">Remarks</span></span>  

 <span data-ttu-id="5c246-120">當您將專案的屬性設定為 [自訂] 來指定自訂的 cookie 處理常式時 `mode` `<cookieHandler>` ，您必須加入 `<customCookieHandler>` 參考 cookie 處理常式類型的子專案，以指定自訂 cookie 處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="5c246-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="5c246-121">當屬性設定為「區塊」或「預設」時，無法指定此元素 `mode` 。</span><span class="sxs-lookup"><span data-stu-id="5c246-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="5c246-122">自訂 cookie 處理常式必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="5c246-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="5c246-123">`<customCookieHandler>`元素是由 <xref:System.IdentityModel.Configuration.CustomTypeElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="5c246-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c246-124">範例</span><span class="sxs-lookup"><span data-stu-id="5c246-124">Example</span></span>  

 <span data-ttu-id="5c246-125">下列範例會將 SAM 設定為使用類型的自訂 cookie 處理常式 `MyNamespace.MyCustomCookieHandler` 。</span><span class="sxs-lookup"><span data-stu-id="5c246-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c246-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c246-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
