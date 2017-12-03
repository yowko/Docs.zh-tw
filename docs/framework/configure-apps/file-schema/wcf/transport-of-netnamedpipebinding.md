---
title: "&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15489d2f5447fc2d3d4fb5173bcc94b5fb68e1c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="1d3ea-102">&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="1d3ea-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="1d3ea-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="1d3ea-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d3ea-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-105">\<bindings></span></span>  
<span data-ttu-id="1d3ea-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="1d3ea-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-107">\<binding></span></span>  
<span data-ttu-id="1d3ea-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-108">\<security></span></span>  
<span data-ttu-id="1d3ea-109">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d3ea-110">語法</span><span class="sxs-lookup"><span data-stu-id="1d3ea-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d3ea-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1d3ea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1d3ea-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d3ea-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1d3ea-113">Attributes</span></span>  
  
|<span data-ttu-id="1d3ea-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1d3ea-114">Attribute</span></span>|<span data-ttu-id="1d3ea-115">描述</span><span class="sxs-lookup"><span data-stu-id="1d3ea-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d3ea-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1d3ea-116">protectionLevel</span></span>|<span data-ttu-id="1d3ea-117">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="1d3ea-118">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1d3ea-119">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1d3ea-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="1d3ea-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1d3ea-121">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-121">-   None: No protection.</span></span><br /><span data-ttu-id="1d3ea-122">-Sign： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1d3ea-123">-EncryptAndSign： 加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1d3ea-124">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d3ea-125">子元素</span><span class="sxs-lookup"><span data-stu-id="1d3ea-125">Child Elements</span></span>  
 <span data-ttu-id="1d3ea-126">無</span><span class="sxs-lookup"><span data-stu-id="1d3ea-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d3ea-127">父項目</span><span class="sxs-lookup"><span data-stu-id="1d3ea-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1d3ea-128">項目</span><span class="sxs-lookup"><span data-stu-id="1d3ea-128">Element</span></span>|<span data-ttu-id="1d3ea-129">說明</span><span class="sxs-lookup"><span data-stu-id="1d3ea-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d3ea-130">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="1d3ea-131">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1d3ea-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d3ea-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3ea-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="1d3ea-133">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="1d3ea-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="1d3ea-134">繫結</span><span class="sxs-lookup"><span data-stu-id="1d3ea-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1d3ea-135">設定系統提供繫結</span><span class="sxs-lookup"><span data-stu-id="1d3ea-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1d3ea-136">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="1d3ea-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="1d3ea-137">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="1d3ea-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
