---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: fa31dda3274c9768694bdf5232f31554899e1d82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203388"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="ec869-102">\<安全性 > 的\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="ec869-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="ec869-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ec869-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="ec869-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ec869-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec869-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ec869-105">\<bindings></span></span>  
<span data-ttu-id="ec869-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="ec869-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="ec869-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ec869-107">\<binding></span></span>  
<span data-ttu-id="ec869-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ec869-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec869-109">語法</span><span class="sxs-lookup"><span data-stu-id="ec869-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec869-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ec869-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ec869-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ec869-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec869-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ec869-112">Attributes</span></span>  
  
|<span data-ttu-id="ec869-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ec869-113">Attribute</span></span>|<span data-ttu-id="ec869-114">描述</span><span class="sxs-lookup"><span data-stu-id="ec869-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec869-115">模式</span><span class="sxs-lookup"><span data-stu-id="ec869-115">mode</span></span>|<span data-ttu-id="ec869-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="ec869-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="ec869-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="ec869-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ec869-118">-None:這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="ec869-118">-   None: This disables security.</span></span><br /><span data-ttu-id="ec869-119">-傳輸：使用基礎傳輸型安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="ec869-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="ec869-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="ec869-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="ec869-121">-預設值是傳輸。</span><span class="sxs-lookup"><span data-stu-id="ec869-121">-   The default value is Transport.</span></span> <span data-ttu-id="ec869-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="ec869-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec869-123">子元素</span><span class="sxs-lookup"><span data-stu-id="ec869-123">Child Elements</span></span>  
  
|<span data-ttu-id="ec869-124">項目</span><span class="sxs-lookup"><span data-stu-id="ec869-124">Element</span></span>|<span data-ttu-id="ec869-125">描述</span><span class="sxs-lookup"><span data-stu-id="ec869-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec869-126">transport</span><span class="sxs-lookup"><span data-stu-id="ec869-126">transport</span></span>|<span data-ttu-id="ec869-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ec869-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="ec869-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="ec869-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec869-129">父項目</span><span class="sxs-lookup"><span data-stu-id="ec869-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ec869-130">項目</span><span class="sxs-lookup"><span data-stu-id="ec869-130">Element</span></span>|<span data-ttu-id="ec869-131">描述</span><span class="sxs-lookup"><span data-stu-id="ec869-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec869-132">繫結</span><span class="sxs-lookup"><span data-stu-id="ec869-132">binding</span></span>|<span data-ttu-id="ec869-133">繫結項目[ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="ec869-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec869-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec869-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="ec869-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="ec869-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ec869-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="ec869-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="ec869-137">繫結</span><span class="sxs-lookup"><span data-stu-id="ec869-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ec869-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="ec869-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ec869-139">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="ec869-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ec869-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="ec869-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
