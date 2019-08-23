---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936679"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="076c9-102">\<netNamedPipeBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="076c9-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="076c9-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="076c9-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="076c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="076c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="076c9-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="076c9-105">\<bindings></span></span>  
<span data-ttu-id="076c9-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="076c9-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="076c9-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="076c9-107">\<binding></span></span>  
<span data-ttu-id="076c9-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="076c9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="076c9-109">語法</span><span class="sxs-lookup"><span data-stu-id="076c9-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="076c9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="076c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="076c9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="076c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="076c9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="076c9-112">Attributes</span></span>  
  
|<span data-ttu-id="076c9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="076c9-113">Attribute</span></span>|<span data-ttu-id="076c9-114">說明</span><span class="sxs-lookup"><span data-stu-id="076c9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="076c9-115">模式</span><span class="sxs-lookup"><span data-stu-id="076c9-115">mode</span></span>|<span data-ttu-id="076c9-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="076c9-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="076c9-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="076c9-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="076c9-118">無這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="076c9-118">-   None: This disables security.</span></span><br /><span data-ttu-id="076c9-119">運送安全性是以基礎傳輸為基礎的安全性來提供。</span><span class="sxs-lookup"><span data-stu-id="076c9-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="076c9-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="076c9-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="076c9-121">-預設值是 Transport。</span><span class="sxs-lookup"><span data-stu-id="076c9-121">-   The default value is Transport.</span></span> <span data-ttu-id="076c9-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="076c9-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="076c9-123">子元素</span><span class="sxs-lookup"><span data-stu-id="076c9-123">Child Elements</span></span>  
  
|<span data-ttu-id="076c9-124">項目</span><span class="sxs-lookup"><span data-stu-id="076c9-124">Element</span></span>|<span data-ttu-id="076c9-125">描述</span><span class="sxs-lookup"><span data-stu-id="076c9-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="076c9-126">transport</span><span class="sxs-lookup"><span data-stu-id="076c9-126">transport</span></span>|<span data-ttu-id="076c9-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="076c9-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="076c9-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="076c9-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="076c9-129">父項目</span><span class="sxs-lookup"><span data-stu-id="076c9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="076c9-130">項目</span><span class="sxs-lookup"><span data-stu-id="076c9-130">Element</span></span>|<span data-ttu-id="076c9-131">描述</span><span class="sxs-lookup"><span data-stu-id="076c9-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="076c9-132">繫結</span><span class="sxs-lookup"><span data-stu-id="076c9-132">binding</span></span>|<span data-ttu-id="076c9-133">NetNamedPipeBinding > 的 binding 元素。 [ \< ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="076c9-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="076c9-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="076c9-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="076c9-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="076c9-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="076c9-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="076c9-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="076c9-137">繫結</span><span class="sxs-lookup"><span data-stu-id="076c9-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="076c9-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="076c9-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="076c9-139">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="076c9-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="076c9-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="076c9-140">\<binding></span></span>](../../../misc/binding.md)
