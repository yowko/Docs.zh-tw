---
title: '&lt;netNamedPipeBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: eee4cc13b5181caa4449c3ad6ebc5247cc7e0f1a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033372"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="58382-102">&lt;netNamedPipeBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="58382-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="58382-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="58382-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="58382-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58382-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="58382-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58382-105">\<bindings></span></span>  
<span data-ttu-id="58382-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="58382-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="58382-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58382-107">\<binding></span></span>  
<span data-ttu-id="58382-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="58382-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58382-109">語法</span><span class="sxs-lookup"><span data-stu-id="58382-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58382-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58382-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58382-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58382-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58382-112">屬性</span><span class="sxs-lookup"><span data-stu-id="58382-112">Attributes</span></span>  
  
|<span data-ttu-id="58382-113">屬性</span><span class="sxs-lookup"><span data-stu-id="58382-113">Attribute</span></span>|<span data-ttu-id="58382-114">描述</span><span class="sxs-lookup"><span data-stu-id="58382-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58382-115">模式</span><span class="sxs-lookup"><span data-stu-id="58382-115">mode</span></span>|<span data-ttu-id="58382-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="58382-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="58382-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="58382-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="58382-118">-None： 這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="58382-118">-   None: This disables security.</span></span><br /><span data-ttu-id="58382-119">-傳輸： 安全性被提供使用基礎傳輸型安全性。</span><span class="sxs-lookup"><span data-stu-id="58382-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="58382-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="58382-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="58382-121">-預設值是傳輸。</span><span class="sxs-lookup"><span data-stu-id="58382-121">-   The default value is Transport.</span></span> <span data-ttu-id="58382-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="58382-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58382-123">子元素</span><span class="sxs-lookup"><span data-stu-id="58382-123">Child Elements</span></span>  
  
|<span data-ttu-id="58382-124">項目</span><span class="sxs-lookup"><span data-stu-id="58382-124">Element</span></span>|<span data-ttu-id="58382-125">描述</span><span class="sxs-lookup"><span data-stu-id="58382-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58382-126">transport</span><span class="sxs-lookup"><span data-stu-id="58382-126">transport</span></span>|<span data-ttu-id="58382-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="58382-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="58382-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="58382-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58382-129">父項目</span><span class="sxs-lookup"><span data-stu-id="58382-129">Parent Elements</span></span>  
  
|<span data-ttu-id="58382-130">項目</span><span class="sxs-lookup"><span data-stu-id="58382-130">Element</span></span>|<span data-ttu-id="58382-131">描述</span><span class="sxs-lookup"><span data-stu-id="58382-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58382-132">繫結</span><span class="sxs-lookup"><span data-stu-id="58382-132">binding</span></span>|<span data-ttu-id="58382-133">繫結項目[ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="58382-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58382-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58382-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="58382-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="58382-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="58382-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="58382-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="58382-137">繫結</span><span class="sxs-lookup"><span data-stu-id="58382-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="58382-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="58382-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="58382-139">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="58382-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="58382-140">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="58382-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
