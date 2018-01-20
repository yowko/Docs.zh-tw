---
title: "&lt;netNamedPipeBinding&gt; 的 &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3a018c502aead84eb6936001acb5bc24c59188f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="7930e-102">&lt;netNamedPipeBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="7930e-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="7930e-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7930e-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="7930e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7930e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7930e-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7930e-105">\<bindings></span></span>  
<span data-ttu-id="7930e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="7930e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="7930e-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="7930e-107">\<binding></span></span>  
<span data-ttu-id="7930e-108">\<security></span><span class="sxs-lookup"><span data-stu-id="7930e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7930e-109">語法</span><span class="sxs-lookup"><span data-stu-id="7930e-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7930e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7930e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7930e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7930e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7930e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7930e-112">Attributes</span></span>  
  
|<span data-ttu-id="7930e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7930e-113">Attribute</span></span>|<span data-ttu-id="7930e-114">描述</span><span class="sxs-lookup"><span data-stu-id="7930e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7930e-115">模式</span><span class="sxs-lookup"><span data-stu-id="7930e-115">mode</span></span>|<span data-ttu-id="7930e-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="7930e-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="7930e-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="7930e-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7930e-118">-None： 這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="7930e-118">-   None: This disables security.</span></span><br /><span data-ttu-id="7930e-119">： 傳輸安全性會使用提供基礎傳輸型安全性。</span><span class="sxs-lookup"><span data-stu-id="7930e-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="7930e-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="7930e-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="7930e-121">-此預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="7930e-121">-   The default value is Transport.</span></span> <span data-ttu-id="7930e-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="7930e-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7930e-123">子元素</span><span class="sxs-lookup"><span data-stu-id="7930e-123">Child Elements</span></span>  
  
|<span data-ttu-id="7930e-124">項目</span><span class="sxs-lookup"><span data-stu-id="7930e-124">Element</span></span>|<span data-ttu-id="7930e-125">描述</span><span class="sxs-lookup"><span data-stu-id="7930e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7930e-126">transport</span><span class="sxs-lookup"><span data-stu-id="7930e-126">transport</span></span>|<span data-ttu-id="7930e-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7930e-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="7930e-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="7930e-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7930e-129">父項目</span><span class="sxs-lookup"><span data-stu-id="7930e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7930e-130">項目</span><span class="sxs-lookup"><span data-stu-id="7930e-130">Element</span></span>|<span data-ttu-id="7930e-131">描述</span><span class="sxs-lookup"><span data-stu-id="7930e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7930e-132">繫結</span><span class="sxs-lookup"><span data-stu-id="7930e-132">binding</span></span>|<span data-ttu-id="7930e-133">繫結項目[ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="7930e-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7930e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="7930e-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="7930e-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7930e-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7930e-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="7930e-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="7930e-137">繫結</span><span class="sxs-lookup"><span data-stu-id="7930e-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7930e-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7930e-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7930e-139">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="7930e-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7930e-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="7930e-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
