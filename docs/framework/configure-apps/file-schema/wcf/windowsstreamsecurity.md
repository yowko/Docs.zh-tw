---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 0f1dfd523e593c82727354db7ce39ffc992bdfb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932797"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="56112-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="56112-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="56112-102">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="56112-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="56112-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="56112-103">\<system.serviceModel></span></span>  
<span data-ttu-id="56112-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="56112-104">\<bindings></span></span>  
<span data-ttu-id="56112-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="56112-105">\<customBinding></span></span>  
<span data-ttu-id="56112-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="56112-106">\<binding></span></span>  
<span data-ttu-id="56112-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="56112-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56112-108">語法</span><span class="sxs-lookup"><span data-stu-id="56112-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56112-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56112-109">Attributes and Elements</span></span>  
 <span data-ttu-id="56112-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56112-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56112-111">屬性</span><span class="sxs-lookup"><span data-stu-id="56112-111">Attributes</span></span>  
  
|<span data-ttu-id="56112-112">屬性</span><span class="sxs-lookup"><span data-stu-id="56112-112">Attribute</span></span>|<span data-ttu-id="56112-113">描述</span><span class="sxs-lookup"><span data-stu-id="56112-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56112-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="56112-114">protectionLevel</span></span>|<span data-ttu-id="56112-115">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="56112-115">Defines message-level security.</span></span> <span data-ttu-id="56112-116">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="56112-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="56112-117">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="56112-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="56112-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="56112-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="56112-119">無無保護。</span><span class="sxs-lookup"><span data-stu-id="56112-119">-   None: No protection.</span></span><br /><span data-ttu-id="56112-120">簽訂訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="56112-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="56112-121">EncryptAndSign訊息會經過簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="56112-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="56112-122">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="56112-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="56112-123">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="56112-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56112-124">子元素</span><span class="sxs-lookup"><span data-stu-id="56112-124">Child Elements</span></span>  
 <span data-ttu-id="56112-125">無</span><span class="sxs-lookup"><span data-stu-id="56112-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56112-126">父項目</span><span class="sxs-lookup"><span data-stu-id="56112-126">Parent Elements</span></span>  
  
|<span data-ttu-id="56112-127">項目</span><span class="sxs-lookup"><span data-stu-id="56112-127">Element</span></span>|<span data-ttu-id="56112-128">描述</span><span class="sxs-lookup"><span data-stu-id="56112-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56112-129">\<binding></span><span class="sxs-lookup"><span data-stu-id="56112-129">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="56112-130">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="56112-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56112-131">備註</span><span class="sxs-lookup"><span data-stu-id="56112-131">Remarks</span></span>  
 <span data-ttu-id="56112-132">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="56112-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="56112-133">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="56112-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="56112-134">此傳輸安全性的設定是由這個 configuration 元素[ \<以及 sslStreamSecurity >](sslstreamsecurity.md)所封裝, 而您可以將其設定並新增至自訂系結</span><span class="sxs-lookup"><span data-stu-id="56112-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56112-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56112-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="56112-136">繫結</span><span class="sxs-lookup"><span data-stu-id="56112-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="56112-137">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="56112-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="56112-138">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="56112-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="56112-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="56112-139">\<customBinding></span></span>](custombinding.md)
