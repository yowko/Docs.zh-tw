---
title: '&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: c42132f774257589b9020248188ee8d972eb92ba
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837046"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="65c0a-102">&lt;netNamedPipeBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="65c0a-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="65c0a-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="65c0a-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="65c0a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="65c0a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="65c0a-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="65c0a-105">\<bindings></span></span>  
<span data-ttu-id="65c0a-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="65c0a-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="65c0a-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="65c0a-107">\<binding></span></span>  
<span data-ttu-id="65c0a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="65c0a-108">\<security></span></span>  
<span data-ttu-id="65c0a-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="65c0a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c0a-110">語法</span><span class="sxs-lookup"><span data-stu-id="65c0a-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65c0a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="65c0a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="65c0a-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="65c0a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65c0a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="65c0a-113">Attributes</span></span>  
  
|<span data-ttu-id="65c0a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="65c0a-114">Attribute</span></span>|<span data-ttu-id="65c0a-115">描述</span><span class="sxs-lookup"><span data-stu-id="65c0a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65c0a-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="65c0a-116">protectionLevel</span></span>|<span data-ttu-id="65c0a-117">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="65c0a-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="65c0a-118">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="65c0a-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="65c0a-119">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="65c0a-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="65c0a-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="65c0a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="65c0a-121">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="65c0a-121">-   None: No protection.</span></span><br /><span data-ttu-id="65c0a-122">簽署： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="65c0a-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="65c0a-123">-EncryptAndSign： 訊息會經過加密及簽署。</span><span class="sxs-lookup"><span data-stu-id="65c0a-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="65c0a-124">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="65c0a-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65c0a-125">子元素</span><span class="sxs-lookup"><span data-stu-id="65c0a-125">Child Elements</span></span>  
 <span data-ttu-id="65c0a-126">無</span><span class="sxs-lookup"><span data-stu-id="65c0a-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65c0a-127">父項目</span><span class="sxs-lookup"><span data-stu-id="65c0a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="65c0a-128">項目</span><span class="sxs-lookup"><span data-stu-id="65c0a-128">Element</span></span>|<span data-ttu-id="65c0a-129">描述</span><span class="sxs-lookup"><span data-stu-id="65c0a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65c0a-130">\<security></span><span class="sxs-lookup"><span data-stu-id="65c0a-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="65c0a-131">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="65c0a-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65c0a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65c0a-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="65c0a-133">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="65c0a-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="65c0a-134">繫結</span><span class="sxs-lookup"><span data-stu-id="65c0a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="65c0a-135">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="65c0a-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="65c0a-136">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="65c0a-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="65c0a-137">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="65c0a-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
