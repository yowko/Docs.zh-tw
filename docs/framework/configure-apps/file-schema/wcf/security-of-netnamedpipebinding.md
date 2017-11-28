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
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="fa602-102">&lt;netNamedPipeBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="fa602-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="fa602-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fa602-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="fa602-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fa602-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa602-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fa602-105">\<bindings></span></span>  
<span data-ttu-id="fa602-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="fa602-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="fa602-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fa602-107">\<binding></span></span>  
<span data-ttu-id="fa602-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="fa602-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa602-109">語法</span><span class="sxs-lookup"><span data-stu-id="fa602-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa602-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa602-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fa602-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fa602-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa602-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fa602-112">Attributes</span></span>  
  
|<span data-ttu-id="fa602-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fa602-113">Attribute</span></span>|<span data-ttu-id="fa602-114">描述</span><span class="sxs-lookup"><span data-stu-id="fa602-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa602-115">模式</span><span class="sxs-lookup"><span data-stu-id="fa602-115">mode</span></span>|<span data-ttu-id="fa602-116">指定套用至這個繫結的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="fa602-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="fa602-117">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="fa602-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fa602-118">-None： 這會停用安全性。</span><span class="sxs-lookup"><span data-stu-id="fa602-118">-   None: This disables security.</span></span><br /><span data-ttu-id="fa602-119">： 傳輸安全性會使用提供基礎傳輸型安全性。</span><span class="sxs-lookup"><span data-stu-id="fa602-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="fa602-120">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="fa602-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="fa602-121">-此預設值為 Transport。</span><span class="sxs-lookup"><span data-stu-id="fa602-121">-   The default value is Transport.</span></span> <span data-ttu-id="fa602-122">此屬性的型別為 <xref:System.ServiceModel.NetNamedPipeSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="fa602-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa602-123">子元素</span><span class="sxs-lookup"><span data-stu-id="fa602-123">Child Elements</span></span>  
  
|<span data-ttu-id="fa602-124">項目</span><span class="sxs-lookup"><span data-stu-id="fa602-124">Element</span></span>|<span data-ttu-id="fa602-125">描述</span><span class="sxs-lookup"><span data-stu-id="fa602-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa602-126">transport</span><span class="sxs-lookup"><span data-stu-id="fa602-126">transport</span></span>|<span data-ttu-id="fa602-127">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="fa602-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="fa602-128">此項目的型別為 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="fa602-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa602-129">父項目</span><span class="sxs-lookup"><span data-stu-id="fa602-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fa602-130">項目</span><span class="sxs-lookup"><span data-stu-id="fa602-130">Element</span></span>|<span data-ttu-id="fa602-131">描述</span><span class="sxs-lookup"><span data-stu-id="fa602-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa602-132">繫結</span><span class="sxs-lookup"><span data-stu-id="fa602-132">binding</span></span>|<span data-ttu-id="fa602-133">繫結項目[ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。</span><span class="sxs-lookup"><span data-stu-id="fa602-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa602-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa602-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="fa602-135">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="fa602-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fa602-136">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="fa602-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="fa602-137">繫結</span><span class="sxs-lookup"><span data-stu-id="fa602-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fa602-138">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="fa602-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fa602-139">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="fa602-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fa602-140">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fa602-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
