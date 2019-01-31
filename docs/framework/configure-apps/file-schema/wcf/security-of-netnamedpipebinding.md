---
title: <security> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: ee2c4161f70c01dc09ac36bbcf6a234f822682d0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265296"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="32777-102">\<安全性 > 的\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="32777-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="32777-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="32777-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="32777-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32777-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32777-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="32777-105">\<bindings></span></span>  
<span data-ttu-id="32777-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="32777-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="32777-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="32777-107">\<binding></span></span>  
<span data-ttu-id="32777-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="32777-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32777-109">語法</span><span class="sxs-lookup"><span data-stu-id="32777-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32777-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="32777-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32777-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="32777-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32777-112">屬性</span><span class="sxs-lookup"><span data-stu-id="32777-112">Attributes</span></span>  
  
|<span data-ttu-id="32777-113">屬性</span><span class="sxs-lookup"><span data-stu-id="32777-113">Attribute</span></span>|<span data-ttu-id="32777-114">描述</span><span class="sxs-lookup"><span data-stu-id="32777-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32777-115">模式</span><span class="sxs-lookup"><span data-stu-id="32777-115">mode</span></span>|<span data-ttu-id="32777-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="32777-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="32777-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="32777-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32777-118">-None:這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="32777-118">-   None: This disables security.</span></span><br /><span data-ttu-id="32777-119">-傳輸：使用基礎傳輸型安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="32777-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="32777-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="32777-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="32777-121">-預設值是傳輸。</span><span class="sxs-lookup"><span data-stu-id="32777-121">-   The default value is Transport.</span></span> <span data-ttu-id="32777-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="32777-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32777-123">子元素</span><span class="sxs-lookup"><span data-stu-id="32777-123">Child Elements</span></span>  
  
|<span data-ttu-id="32777-124">項目</span><span class="sxs-lookup"><span data-stu-id="32777-124">Element</span></span>|<span data-ttu-id="32777-125">描述</span><span class="sxs-lookup"><span data-stu-id="32777-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32777-126">transport</span><span class="sxs-lookup"><span data-stu-id="32777-126">transport</span></span>|<span data-ttu-id="32777-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="32777-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="32777-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="32777-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32777-129">父項目</span><span class="sxs-lookup"><span data-stu-id="32777-129">Parent Elements</span></span>  
  
|<span data-ttu-id="32777-130">項目</span><span class="sxs-lookup"><span data-stu-id="32777-130">Element</span></span>|<span data-ttu-id="32777-131">描述</span><span class="sxs-lookup"><span data-stu-id="32777-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32777-132">繫結</span><span class="sxs-lookup"><span data-stu-id="32777-132">binding</span></span>|<span data-ttu-id="32777-133">繫結項目[ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="32777-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32777-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32777-134">See also</span></span>
- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="32777-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="32777-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="32777-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="32777-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="32777-137">繫結</span><span class="sxs-lookup"><span data-stu-id="32777-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="32777-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="32777-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="32777-139">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="32777-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="32777-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="32777-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
