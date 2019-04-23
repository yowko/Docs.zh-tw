---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199819"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="1c8e3-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1c8e3-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="1c8e3-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="1c8e3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1c8e3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c8e3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1c8e3-105">\<bindings></span></span>  
<span data-ttu-id="1c8e3-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1c8e3-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="1c8e3-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="1c8e3-107">\<binding></span></span>  
<span data-ttu-id="1c8e3-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1c8e3-108">\<security></span></span>  
<span data-ttu-id="1c8e3-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="1c8e3-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8e3-110">語法</span><span class="sxs-lookup"><span data-stu-id="1c8e3-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c8e3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1c8e3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c8e3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c8e3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1c8e3-113">Attributes</span></span>  
  
|<span data-ttu-id="1c8e3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1c8e3-114">Attribute</span></span>|<span data-ttu-id="1c8e3-115">描述</span><span class="sxs-lookup"><span data-stu-id="1c8e3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c8e3-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1c8e3-116">protectionLevel</span></span>|<span data-ttu-id="1c8e3-117">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="1c8e3-118">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1c8e3-119">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1c8e3-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="1c8e3-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c8e3-121">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-121">-   None: No protection.</span></span><br /><span data-ttu-id="1c8e3-122">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1c8e3-123">-EncryptAndSign:訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1c8e3-124">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c8e3-125">子元素</span><span class="sxs-lookup"><span data-stu-id="1c8e3-125">Child Elements</span></span>  
 <span data-ttu-id="1c8e3-126">None</span><span class="sxs-lookup"><span data-stu-id="1c8e3-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c8e3-127">父項目</span><span class="sxs-lookup"><span data-stu-id="1c8e3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1c8e3-128">項目</span><span class="sxs-lookup"><span data-stu-id="1c8e3-128">Element</span></span>|<span data-ttu-id="1c8e3-129">描述</span><span class="sxs-lookup"><span data-stu-id="1c8e3-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c8e3-130">\<security></span><span class="sxs-lookup"><span data-stu-id="1c8e3-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="1c8e3-131">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1c8e3-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c8e3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c8e3-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="1c8e3-133">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="1c8e3-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1c8e3-134">繫結</span><span class="sxs-lookup"><span data-stu-id="1c8e3-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1c8e3-135">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="1c8e3-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1c8e3-136">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="1c8e3-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1c8e3-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="1c8e3-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
