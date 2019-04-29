---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788345"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="03b01-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="03b01-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="03b01-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="03b01-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="03b01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="03b01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="03b01-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="03b01-105">\<bindings></span></span>  
<span data-ttu-id="03b01-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="03b01-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="03b01-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="03b01-107">\<binding></span></span>  
<span data-ttu-id="03b01-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="03b01-108">\<security></span></span>  
<span data-ttu-id="03b01-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="03b01-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b01-110">語法</span><span class="sxs-lookup"><span data-stu-id="03b01-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b01-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03b01-111">Attributes and Elements</span></span>  
 <span data-ttu-id="03b01-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="03b01-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b01-113">屬性</span><span class="sxs-lookup"><span data-stu-id="03b01-113">Attributes</span></span>  
  
|<span data-ttu-id="03b01-114">屬性</span><span class="sxs-lookup"><span data-stu-id="03b01-114">Attribute</span></span>|<span data-ttu-id="03b01-115">描述</span><span class="sxs-lookup"><span data-stu-id="03b01-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03b01-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="03b01-116">protectionLevel</span></span>|<span data-ttu-id="03b01-117">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="03b01-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="03b01-118">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="03b01-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="03b01-119">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="03b01-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="03b01-120">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="03b01-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="03b01-121">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="03b01-121">-   None: No protection.</span></span><br /><span data-ttu-id="03b01-122">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="03b01-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="03b01-123">-EncryptAndSign:訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="03b01-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="03b01-124">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="03b01-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03b01-125">子元素</span><span class="sxs-lookup"><span data-stu-id="03b01-125">Child Elements</span></span>  
 <span data-ttu-id="03b01-126">None</span><span class="sxs-lookup"><span data-stu-id="03b01-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03b01-127">父項目</span><span class="sxs-lookup"><span data-stu-id="03b01-127">Parent Elements</span></span>  
  
|<span data-ttu-id="03b01-128">項目</span><span class="sxs-lookup"><span data-stu-id="03b01-128">Element</span></span>|<span data-ttu-id="03b01-129">描述</span><span class="sxs-lookup"><span data-stu-id="03b01-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b01-130">\<security></span><span class="sxs-lookup"><span data-stu-id="03b01-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="03b01-131">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="03b01-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03b01-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03b01-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="03b01-133">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="03b01-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="03b01-134">繫結</span><span class="sxs-lookup"><span data-stu-id="03b01-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="03b01-135">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="03b01-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="03b01-136">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="03b01-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="03b01-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="03b01-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
