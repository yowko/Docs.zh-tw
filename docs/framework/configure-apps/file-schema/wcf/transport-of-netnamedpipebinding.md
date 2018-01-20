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
ms.workload: dotnet
ms.openlocfilehash: 84811c70f2f3608c10d8886900169f804a8c9b62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="84548-102">&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="84548-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="84548-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="84548-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="84548-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84548-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84548-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="84548-105">\<bindings></span></span>  
<span data-ttu-id="84548-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="84548-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="84548-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="84548-107">\<binding></span></span>  
<span data-ttu-id="84548-108">\<security></span><span class="sxs-lookup"><span data-stu-id="84548-108">\<security></span></span>  
<span data-ttu-id="84548-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="84548-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84548-110">語法</span><span class="sxs-lookup"><span data-stu-id="84548-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84548-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84548-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84548-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84548-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84548-113">屬性</span><span class="sxs-lookup"><span data-stu-id="84548-113">Attributes</span></span>  
  
|<span data-ttu-id="84548-114">屬性</span><span class="sxs-lookup"><span data-stu-id="84548-114">Attribute</span></span>|<span data-ttu-id="84548-115">描述</span><span class="sxs-lookup"><span data-stu-id="84548-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="84548-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="84548-116">protectionLevel</span></span>|<span data-ttu-id="84548-117">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="84548-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="84548-118">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="84548-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="84548-119">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="84548-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="84548-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="84548-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="84548-121">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="84548-121">-   None: No protection.</span></span><br /><span data-ttu-id="84548-122">-Sign： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="84548-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="84548-123">-EncryptAndSign： 加密和訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="84548-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="84548-124">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="84548-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84548-125">子元素</span><span class="sxs-lookup"><span data-stu-id="84548-125">Child Elements</span></span>  
 <span data-ttu-id="84548-126">無</span><span class="sxs-lookup"><span data-stu-id="84548-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84548-127">父項目</span><span class="sxs-lookup"><span data-stu-id="84548-127">Parent Elements</span></span>  
  
|<span data-ttu-id="84548-128">項目</span><span class="sxs-lookup"><span data-stu-id="84548-128">Element</span></span>|<span data-ttu-id="84548-129">描述</span><span class="sxs-lookup"><span data-stu-id="84548-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84548-130">\<security></span><span class="sxs-lookup"><span data-stu-id="84548-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="84548-131">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="84548-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84548-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="84548-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="84548-133">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="84548-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="84548-134">繫結</span><span class="sxs-lookup"><span data-stu-id="84548-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="84548-135">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="84548-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="84548-136">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="84548-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="84548-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="84548-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
