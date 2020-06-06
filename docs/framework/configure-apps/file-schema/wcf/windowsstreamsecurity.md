---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735891"
---
# \<windowsStreamSecurity>
<span data-ttu-id="3c9ba-101">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="3c9ba-102">語法</span><span class="sxs-lookup"><span data-stu-id="3c9ba-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c9ba-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3c9ba-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3c9ba-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c9ba-105">屬性</span><span class="sxs-lookup"><span data-stu-id="3c9ba-105">Attributes</span></span>  
  
|<span data-ttu-id="3c9ba-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3c9ba-106">Attribute</span></span>|<span data-ttu-id="3c9ba-107">描述</span><span class="sxs-lookup"><span data-stu-id="3c9ba-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c9ba-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3c9ba-108">protectionLevel</span></span>|<span data-ttu-id="3c9ba-109">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-109">Defines message-level security.</span></span> <span data-ttu-id="3c9ba-110">簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3c9ba-111">加密可在傳輸時提供資料等級的隱私權。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="3c9ba-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="3c9ba-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3c9ba-113">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-113">-   None: No protection.</span></span><br /><span data-ttu-id="3c9ba-114">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3c9ba-115">-EncryptAndSign：訊息已簽署並加密。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="3c9ba-116">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="3c9ba-117">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c9ba-118">子元素</span><span class="sxs-lookup"><span data-stu-id="3c9ba-118">Child Elements</span></span>  
 <span data-ttu-id="3c9ba-119">無</span><span class="sxs-lookup"><span data-stu-id="3c9ba-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c9ba-120">父項目</span><span class="sxs-lookup"><span data-stu-id="3c9ba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3c9ba-121">元素</span><span class="sxs-lookup"><span data-stu-id="3c9ba-121">Element</span></span>|<span data-ttu-id="3c9ba-122">描述</span><span class="sxs-lookup"><span data-stu-id="3c9ba-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3c9ba-123">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c9ba-124">備註</span><span class="sxs-lookup"><span data-stu-id="3c9ba-124">Remarks</span></span>  
 <span data-ttu-id="3c9ba-125">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="3c9ba-126">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="3c9ba-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="3c9ba-127">此傳輸安全性的設定是由這個 configuration 專案和所封裝，而您 [\<sslStreamSecurity>](sslstreamsecurity.md) 可以將其設定並新增至自訂系結</span><span class="sxs-lookup"><span data-stu-id="3c9ba-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c9ba-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c9ba-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="3c9ba-129">繫結</span><span class="sxs-lookup"><span data-stu-id="3c9ba-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c9ba-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="3c9ba-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3c9ba-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3c9ba-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
