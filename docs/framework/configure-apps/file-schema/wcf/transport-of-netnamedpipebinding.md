---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 6ea0b1e374659bbbbb2f47630c009f823ccd4de9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399335"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="376a8-102">\<netNamedPipeBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="376a8-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="376a8-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="376a8-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="376a8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="376a8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="376a8-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="376a8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="376a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="376a8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="376a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="376a8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="376a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="376a8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="376a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="376a8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="376a8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="376a8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="376a8-111">語法</span><span class="sxs-lookup"><span data-stu-id="376a8-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="376a8-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="376a8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="376a8-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="376a8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="376a8-114">屬性</span><span class="sxs-lookup"><span data-stu-id="376a8-114">Attributes</span></span>  
  
|<span data-ttu-id="376a8-115">屬性</span><span class="sxs-lookup"><span data-stu-id="376a8-115">Attribute</span></span>|<span data-ttu-id="376a8-116">描述</span><span class="sxs-lookup"><span data-stu-id="376a8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="376a8-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="376a8-117">protectionLevel</span></span>|<span data-ttu-id="376a8-118">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="376a8-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="376a8-119">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="376a8-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="376a8-120">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="376a8-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="376a8-121">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="376a8-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="376a8-122">無無保護。</span><span class="sxs-lookup"><span data-stu-id="376a8-122">-   None: No protection.</span></span><br /><span data-ttu-id="376a8-123">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="376a8-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="376a8-124">EncryptAndSign訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="376a8-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="376a8-125">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="376a8-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="376a8-126">子元素</span><span class="sxs-lookup"><span data-stu-id="376a8-126">Child Elements</span></span>  
 <span data-ttu-id="376a8-127">無</span><span class="sxs-lookup"><span data-stu-id="376a8-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="376a8-128">父項目</span><span class="sxs-lookup"><span data-stu-id="376a8-128">Parent Elements</span></span>  
  
|<span data-ttu-id="376a8-129">項目</span><span class="sxs-lookup"><span data-stu-id="376a8-129">Element</span></span>|<span data-ttu-id="376a8-130">描述</span><span class="sxs-lookup"><span data-stu-id="376a8-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="376a8-131">\<security></span><span class="sxs-lookup"><span data-stu-id="376a8-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="376a8-132">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="376a8-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="376a8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="376a8-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="376a8-134">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="376a8-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="376a8-135">繫結</span><span class="sxs-lookup"><span data-stu-id="376a8-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="376a8-136">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="376a8-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="376a8-137">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="376a8-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="376a8-138">\<binding></span><span class="sxs-lookup"><span data-stu-id="376a8-138">\<binding></span></span>](../../../misc/binding.md)
