---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113629"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="365f5-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="365f5-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="365f5-102">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="365f5-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="365f5-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="365f5-103">\<system.serviceModel></span></span>  
<span data-ttu-id="365f5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="365f5-104">\<bindings></span></span>  
<span data-ttu-id="365f5-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="365f5-105">\<customBinding></span></span>  
<span data-ttu-id="365f5-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="365f5-106">\<binding></span></span>  
<span data-ttu-id="365f5-107">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="365f5-107">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365f5-108">語法</span><span class="sxs-lookup"><span data-stu-id="365f5-108">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="365f5-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="365f5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="365f5-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="365f5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="365f5-111">屬性</span><span class="sxs-lookup"><span data-stu-id="365f5-111">Attributes</span></span>  
  
|<span data-ttu-id="365f5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="365f5-112">Attribute</span></span>|<span data-ttu-id="365f5-113">描述</span><span class="sxs-lookup"><span data-stu-id="365f5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="365f5-114">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="365f5-114">protectionLevel</span></span>|<span data-ttu-id="365f5-115">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="365f5-115">Defines message-level security.</span></span> <span data-ttu-id="365f5-116">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="365f5-116">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="365f5-117">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="365f5-117">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="365f5-118">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="365f5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="365f5-119">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="365f5-119">-   None: No protection.</span></span><br /><span data-ttu-id="365f5-120">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="365f5-120">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="365f5-121">-EncryptAndSign:訊息已簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="365f5-121">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="365f5-122">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="365f5-122">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="365f5-123">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="365f5-123">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="365f5-124">子元素</span><span class="sxs-lookup"><span data-stu-id="365f5-124">Child Elements</span></span>  
 <span data-ttu-id="365f5-125">None</span><span class="sxs-lookup"><span data-stu-id="365f5-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="365f5-126">父項目</span><span class="sxs-lookup"><span data-stu-id="365f5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="365f5-127">項目</span><span class="sxs-lookup"><span data-stu-id="365f5-127">Element</span></span>|<span data-ttu-id="365f5-128">描述</span><span class="sxs-lookup"><span data-stu-id="365f5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="365f5-129">\<binding></span><span class="sxs-lookup"><span data-stu-id="365f5-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="365f5-130">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="365f5-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="365f5-131">備註</span><span class="sxs-lookup"><span data-stu-id="365f5-131">Remarks</span></span>  
 <span data-ttu-id="365f5-132">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="365f5-132">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="365f5-133">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="365f5-133">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="365f5-134">此傳輸安全性的組態和封裝這個組態項目[ \<Custombinding> >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)，這可以設定並新增至自訂繫結</span><span class="sxs-lookup"><span data-stu-id="365f5-134">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365f5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="365f5-135">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="365f5-136">繫結</span><span class="sxs-lookup"><span data-stu-id="365f5-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="365f5-137">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="365f5-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="365f5-138">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="365f5-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="365f5-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="365f5-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
