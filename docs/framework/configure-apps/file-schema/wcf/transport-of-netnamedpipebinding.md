---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735968"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="efbfb-102">\<transport> 的 \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="efbfb-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="efbfb-103">定義具名管道的傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="efbfb-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="efbfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="efbfb-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efbfb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="efbfb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="efbfb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="efbfb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efbfb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="efbfb-107">Attributes</span></span>  
  
|<span data-ttu-id="efbfb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="efbfb-108">Attribute</span></span>|<span data-ttu-id="efbfb-109">描述</span><span class="sxs-lookup"><span data-stu-id="efbfb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efbfb-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="efbfb-110">protectionLevel</span></span>|<span data-ttu-id="efbfb-111">定義具名管道的保護層級。</span><span class="sxs-lookup"><span data-stu-id="efbfb-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="efbfb-112">簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="efbfb-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="efbfb-113">加密可在傳輸時提供資料等級的隱私權。</span><span class="sxs-lookup"><span data-stu-id="efbfb-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="efbfb-114">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="efbfb-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efbfb-115">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="efbfb-115">-   None: No protection.</span></span><br /><span data-ttu-id="efbfb-116">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="efbfb-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="efbfb-117">-EncryptAndSign：訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="efbfb-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="efbfb-118">預設值為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="efbfb-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efbfb-119">子元素</span><span class="sxs-lookup"><span data-stu-id="efbfb-119">Child Elements</span></span>  
 <span data-ttu-id="efbfb-120">無</span><span class="sxs-lookup"><span data-stu-id="efbfb-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efbfb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="efbfb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="efbfb-122">元素</span><span class="sxs-lookup"><span data-stu-id="efbfb-122">Element</span></span>|<span data-ttu-id="efbfb-123">描述</span><span class="sxs-lookup"><span data-stu-id="efbfb-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="efbfb-124">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="efbfb-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efbfb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efbfb-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="efbfb-126">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="efbfb-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="efbfb-127">繫結</span><span class="sxs-lookup"><span data-stu-id="efbfb-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="efbfb-128">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="efbfb-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="efbfb-129">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="efbfb-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
