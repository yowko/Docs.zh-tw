---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735968"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="d59b6-102">\<netNamedPipeBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="d59b6-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="d59b6-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d59b6-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="d59b6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d59b6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d59b6-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d59b6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d59b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="d59b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d59b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="d59b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="d59b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="d59b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d59b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="d59b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="d59b6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="d59b6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59b6-111">語法</span><span class="sxs-lookup"><span data-stu-id="d59b6-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d59b6-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d59b6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d59b6-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d59b6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d59b6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d59b6-114">Attributes</span></span>  
  
|<span data-ttu-id="d59b6-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d59b6-115">Attribute</span></span>|<span data-ttu-id="d59b6-116">描述</span><span class="sxs-lookup"><span data-stu-id="d59b6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d59b6-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="d59b6-117">protectionLevel</span></span>|<span data-ttu-id="d59b6-118">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="d59b6-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="d59b6-119">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="d59b6-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="d59b6-120">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="d59b6-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="d59b6-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="d59b6-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d59b6-122">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="d59b6-122">-   None: No protection.</span></span><br /><span data-ttu-id="d59b6-123">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="d59b6-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d59b6-124">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="d59b6-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="d59b6-125">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="d59b6-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d59b6-126">子項目</span><span class="sxs-lookup"><span data-stu-id="d59b6-126">Child Elements</span></span>  
 <span data-ttu-id="d59b6-127">None</span><span class="sxs-lookup"><span data-stu-id="d59b6-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d59b6-128">父項目</span><span class="sxs-lookup"><span data-stu-id="d59b6-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d59b6-129">項目</span><span class="sxs-lookup"><span data-stu-id="d59b6-129">Element</span></span>|<span data-ttu-id="d59b6-130">描述</span><span class="sxs-lookup"><span data-stu-id="d59b6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d59b6-131">\<security ></span><span class="sxs-lookup"><span data-stu-id="d59b6-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="d59b6-132">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="d59b6-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d59b6-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="d59b6-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="d59b6-134">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d59b6-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d59b6-135">繫結</span><span class="sxs-lookup"><span data-stu-id="d59b6-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d59b6-136">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d59b6-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d59b6-137">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d59b6-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d59b6-138">\<binding ></span><span class="sxs-lookup"><span data-stu-id="d59b6-138">\<binding></span></span>](bindings.md)
