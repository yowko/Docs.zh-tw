---
title: '&lt;windowsstreamsecurity 正在&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a089a6fb61e8f7fac4116b2280a5c2fe0b703f94
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755106"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="798c7-102">&lt;windowsstreamsecurity 正在&gt;</span><span class="sxs-lookup"><span data-stu-id="798c7-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="798c7-103">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="798c7-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="798c7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="798c7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="798c7-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="798c7-105">\<bindings></span></span>  
<span data-ttu-id="798c7-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="798c7-106">\<customBinding></span></span>  
<span data-ttu-id="798c7-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="798c7-107">\<binding></span></span>  
<span data-ttu-id="798c7-108">\<windowsstreamsecurity 正在 ></span><span class="sxs-lookup"><span data-stu-id="798c7-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="798c7-109">語法</span><span class="sxs-lookup"><span data-stu-id="798c7-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="798c7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="798c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="798c7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="798c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="798c7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="798c7-112">Attributes</span></span>  
  
|<span data-ttu-id="798c7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="798c7-113">Attribute</span></span>|<span data-ttu-id="798c7-114">描述</span><span class="sxs-lookup"><span data-stu-id="798c7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="798c7-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="798c7-115">protectionLevel</span></span>|<span data-ttu-id="798c7-116">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="798c7-116">Defines message-level security.</span></span> <span data-ttu-id="798c7-117">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="798c7-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="798c7-118">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="798c7-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="798c7-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="798c7-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="798c7-120">-None： 無保護。</span><span class="sxs-lookup"><span data-stu-id="798c7-120">-   None: No protection.</span></span><br /><span data-ttu-id="798c7-121">-Sign： 簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="798c7-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="798c7-122">-EncryptAndSign： 訊息已簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="798c7-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="798c7-123">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="798c7-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="798c7-124">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="798c7-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="798c7-125">子項目</span><span class="sxs-lookup"><span data-stu-id="798c7-125">Child Elements</span></span>  
 <span data-ttu-id="798c7-126">無</span><span class="sxs-lookup"><span data-stu-id="798c7-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="798c7-127">父項目</span><span class="sxs-lookup"><span data-stu-id="798c7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="798c7-128">項目</span><span class="sxs-lookup"><span data-stu-id="798c7-128">Element</span></span>|<span data-ttu-id="798c7-129">描述</span><span class="sxs-lookup"><span data-stu-id="798c7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="798c7-130">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="798c7-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="798c7-131">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="798c7-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="798c7-132">備註</span><span class="sxs-lookup"><span data-stu-id="798c7-132">Remarks</span></span>  
 <span data-ttu-id="798c7-133">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="798c7-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="798c7-134">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="798c7-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="798c7-135">此傳輸安全性的組態由此此組態項目以及[ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)，其中可以設定並新增至自訂繫結</span><span class="sxs-lookup"><span data-stu-id="798c7-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798c7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="798c7-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="798c7-137">繫結</span><span class="sxs-lookup"><span data-stu-id="798c7-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="798c7-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="798c7-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="798c7-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="798c7-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="798c7-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="798c7-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
