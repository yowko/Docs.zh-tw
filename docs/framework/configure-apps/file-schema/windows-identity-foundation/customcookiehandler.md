---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252010"
---
# \<customCookieHandler>
<span data-ttu-id="f773b-101">設定自訂 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="f773b-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="f773b-102">只有當 `mode` 元素的屬性 `<cookieHandler>` 是 "Custom" 時，才會出現此元素。</span><span class="sxs-lookup"><span data-stu-id="f773b-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="f773b-103">自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="f773b-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="f773b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f773b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f773b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f773b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f773b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f773b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f773b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f773b-107">Attributes</span></span>  
  
|<span data-ttu-id="f773b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f773b-108">Attribute</span></span>|<span data-ttu-id="f773b-109">描述</span><span class="sxs-lookup"><span data-stu-id="f773b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f773b-110">type</span><span class="sxs-lookup"><span data-stu-id="f773b-110">type</span></span>|<span data-ttu-id="f773b-111">指定衍生自類別的自訂類型 <xref:System.IdentityModel.Services.CookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="f773b-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="f773b-112">如需如何指定屬性的詳細資訊 `type` ，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f773b-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f773b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f773b-113">Child Elements</span></span>  
 <span data-ttu-id="f773b-114">無</span><span class="sxs-lookup"><span data-stu-id="f773b-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f773b-115">父項目</span><span class="sxs-lookup"><span data-stu-id="f773b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f773b-116">元素</span><span class="sxs-lookup"><span data-stu-id="f773b-116">Element</span></span>|<span data-ttu-id="f773b-117">描述</span><span class="sxs-lookup"><span data-stu-id="f773b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="f773b-118">設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 用來讀取和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="f773b-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f773b-119">備註</span><span class="sxs-lookup"><span data-stu-id="f773b-119">Remarks</span></span>  
 <span data-ttu-id="f773b-120">當您藉由將專案的屬性設定為 "Custom" 來指定自訂 cookie 處理常式時 `mode` `<cookieHandler>` ，您必須包含 `<customCookieHandler>` 參考 cookie 處理常式類型的子項目，以指定自訂 cookie 處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="f773b-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="f773b-121">當 `mode` 屬性設定為 "分塊" 或 "Default" 時，無法指定此元素。</span><span class="sxs-lookup"><span data-stu-id="f773b-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="f773b-122">自訂 cookie 處理常式必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="f773b-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="f773b-123">`<customCookieHandler>`元素是由 <xref:System.IdentityModel.Configuration.CustomTypeElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="f773b-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f773b-124">範例</span><span class="sxs-lookup"><span data-stu-id="f773b-124">Example</span></span>  
 <span data-ttu-id="f773b-125">下列範例會將 SAM 設定為使用類型的自訂 cookie 處理常式 `MyNamespace.MyCustomCookieHandler` 。</span><span class="sxs-lookup"><span data-stu-id="f773b-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f773b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f773b-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
