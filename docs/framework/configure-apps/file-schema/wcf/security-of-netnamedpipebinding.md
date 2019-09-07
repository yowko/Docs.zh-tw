---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: cd3ff5d3983283f9b4783912b4b9525c5000df61
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399820"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="cbdd0-102">\<netNamedPipeBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="cbdd0-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="cbdd0-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="cbdd0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cbdd0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cbdd0-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cbdd0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cbdd0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cbdd0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cbdd0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="cbdd0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="cbdd0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="cbdd0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cbdd0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="cbdd0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbdd0-110">語法</span><span class="sxs-lookup"><span data-stu-id="cbdd0-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbdd0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cbdd0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cbdd0-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbdd0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cbdd0-113">Attributes</span></span>  
  
|<span data-ttu-id="cbdd0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cbdd0-114">Attribute</span></span>|<span data-ttu-id="cbdd0-115">描述</span><span class="sxs-lookup"><span data-stu-id="cbdd0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbdd0-116">模式</span><span class="sxs-lookup"><span data-stu-id="cbdd0-116">mode</span></span>|<span data-ttu-id="cbdd0-117">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="cbdd0-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="cbdd0-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cbdd0-119">無這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-119">-   None: This disables security.</span></span><br /><span data-ttu-id="cbdd0-120">運送安全性是以基礎傳輸為基礎的安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="cbdd0-121">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="cbdd0-122">-預設值是 Transport。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-122">-   The default value is Transport.</span></span> <span data-ttu-id="cbdd0-123">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbdd0-124">子元素</span><span class="sxs-lookup"><span data-stu-id="cbdd0-124">Child Elements</span></span>  
  
|<span data-ttu-id="cbdd0-125">項目</span><span class="sxs-lookup"><span data-stu-id="cbdd0-125">Element</span></span>|<span data-ttu-id="cbdd0-126">說明</span><span class="sxs-lookup"><span data-stu-id="cbdd0-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbdd0-127">transport</span><span class="sxs-lookup"><span data-stu-id="cbdd0-127">transport</span></span>|<span data-ttu-id="cbdd0-128">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="cbdd0-129">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="cbdd0-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbdd0-130">父項目</span><span class="sxs-lookup"><span data-stu-id="cbdd0-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cbdd0-131">項目</span><span class="sxs-lookup"><span data-stu-id="cbdd0-131">Element</span></span>|<span data-ttu-id="cbdd0-132">描述</span><span class="sxs-lookup"><span data-stu-id="cbdd0-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbdd0-133">繫結</span><span class="sxs-lookup"><span data-stu-id="cbdd0-133">binding</span></span>|<span data-ttu-id="cbdd0-134">NetNamedPipeBinding > 的 binding 元素。 [ \< ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="cbdd0-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbdd0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbdd0-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="cbdd0-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="cbdd0-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cbdd0-137">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="cbdd0-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="cbdd0-138">繫結</span><span class="sxs-lookup"><span data-stu-id="cbdd0-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cbdd0-139">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="cbdd0-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cbdd0-140">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="cbdd0-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="cbdd0-141">\<binding></span><span class="sxs-lookup"><span data-stu-id="cbdd0-141">\<binding></span></span>](../../../misc/binding.md)
