---
title: '&lt;windowsStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 4218072f63cabe511ca9d30c77395f734d961eca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745177"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="6669c-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="6669c-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="6669c-103">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6669c-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="6669c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6669c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6669c-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6669c-105">\<bindings></span></span>  
<span data-ttu-id="6669c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6669c-106">\<customBinding></span></span>  
<span data-ttu-id="6669c-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="6669c-107">\<binding></span></span>  
<span data-ttu-id="6669c-108">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="6669c-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6669c-109">語法</span><span class="sxs-lookup"><span data-stu-id="6669c-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6669c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6669c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6669c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6669c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6669c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6669c-112">Attributes</span></span>  
  
|<span data-ttu-id="6669c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6669c-113">Attribute</span></span>|<span data-ttu-id="6669c-114">描述</span><span class="sxs-lookup"><span data-stu-id="6669c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6669c-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="6669c-115">protectionLevel</span></span>|<span data-ttu-id="6669c-116">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="6669c-116">Defines message-level security.</span></span> <span data-ttu-id="6669c-117">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="6669c-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="6669c-118">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="6669c-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="6669c-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="6669c-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6669c-120">-None:無保護。</span><span class="sxs-lookup"><span data-stu-id="6669c-120">-   None: No protection.</span></span><br /><span data-ttu-id="6669c-121">簽署：訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="6669c-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="6669c-122">-EncryptAndSign:訊息已簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="6669c-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="6669c-123">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="6669c-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="6669c-124">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="6669c-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6669c-125">子元素</span><span class="sxs-lookup"><span data-stu-id="6669c-125">Child Elements</span></span>  
 <span data-ttu-id="6669c-126">無</span><span class="sxs-lookup"><span data-stu-id="6669c-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6669c-127">父項目</span><span class="sxs-lookup"><span data-stu-id="6669c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6669c-128">項目</span><span class="sxs-lookup"><span data-stu-id="6669c-128">Element</span></span>|<span data-ttu-id="6669c-129">描述</span><span class="sxs-lookup"><span data-stu-id="6669c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6669c-130">\<binding></span><span class="sxs-lookup"><span data-stu-id="6669c-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6669c-131">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="6669c-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6669c-132">備註</span><span class="sxs-lookup"><span data-stu-id="6669c-132">Remarks</span></span>  
 <span data-ttu-id="6669c-133">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="6669c-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="6669c-134">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="6669c-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="6669c-135">此傳輸安全性的組態和封裝這個組態項目[ \<Custombinding> >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)，這可以設定並新增至自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6669c-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6669c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6669c-136">See also</span></span>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="6669c-137">繫結</span><span class="sxs-lookup"><span data-stu-id="6669c-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6669c-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6669c-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6669c-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6669c-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6669c-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6669c-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
