---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 3c82bd81bd0fabf10f2dd835188b346f62d038b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167076"
---
# \<windowsStreamSecurity>

<span data-ttu-id="1407c-101">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="1407c-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="1407c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1407c-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1407c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1407c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1407c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1407c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1407c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1407c-105">Attributes</span></span>  
  
|<span data-ttu-id="1407c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1407c-106">Attribute</span></span>|<span data-ttu-id="1407c-107">描述</span><span class="sxs-lookup"><span data-stu-id="1407c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1407c-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1407c-108">protectionLevel</span></span>|<span data-ttu-id="1407c-109">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="1407c-109">Defines message-level security.</span></span> <span data-ttu-id="1407c-110">簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="1407c-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1407c-111">加密可在傳輸時提供資料等級的隱私權。</span><span class="sxs-lookup"><span data-stu-id="1407c-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1407c-112">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="1407c-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1407c-113">-None：無保護。</span><span class="sxs-lookup"><span data-stu-id="1407c-113">-   None: No protection.</span></span><br /><span data-ttu-id="1407c-114">-Sign：簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="1407c-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1407c-115">-EncryptAndSign：已簽署和加密訊息。</span><span class="sxs-lookup"><span data-stu-id="1407c-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="1407c-116">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="1407c-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="1407c-117">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="1407c-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1407c-118">子元素</span><span class="sxs-lookup"><span data-stu-id="1407c-118">Child Elements</span></span>  

 <span data-ttu-id="1407c-119">無</span><span class="sxs-lookup"><span data-stu-id="1407c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1407c-120">父項目</span><span class="sxs-lookup"><span data-stu-id="1407c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1407c-121">項目</span><span class="sxs-lookup"><span data-stu-id="1407c-121">Element</span></span>|<span data-ttu-id="1407c-122">描述</span><span class="sxs-lookup"><span data-stu-id="1407c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1407c-123">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="1407c-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1407c-124">備註</span><span class="sxs-lookup"><span data-stu-id="1407c-124">Remarks</span></span>  

 <span data-ttu-id="1407c-125">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="1407c-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="1407c-126">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="1407c-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="1407c-127">此傳輸安全性的設定是由這個設定元素以及 [\<sslStreamSecurity>](sslstreamsecurity.md) 可以設定並新增至自訂系結的所封裝。</span><span class="sxs-lookup"><span data-stu-id="1407c-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1407c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1407c-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="1407c-129">繫結</span><span class="sxs-lookup"><span data-stu-id="1407c-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1407c-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="1407c-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1407c-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="1407c-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
