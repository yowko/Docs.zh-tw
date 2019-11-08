---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735891"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="28659-101">\<Windowsstreamsecurity 正在 ></span><span class="sxs-lookup"><span data-stu-id="28659-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="28659-102">指定自訂繫結的 Windows 資料流安全性設定。</span><span class="sxs-lookup"><span data-stu-id="28659-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="28659-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28659-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28659-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="28659-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="28659-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="28659-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="28659-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="28659-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="28659-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="28659-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="28659-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsstreamsecurity 正在 >**</span><span class="sxs-lookup"><span data-stu-id="28659-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28659-109">語法</span><span class="sxs-lookup"><span data-stu-id="28659-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28659-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="28659-110">Attributes and Elements</span></span>  
 <span data-ttu-id="28659-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="28659-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28659-112">屬性</span><span class="sxs-lookup"><span data-stu-id="28659-112">Attributes</span></span>  
  
|<span data-ttu-id="28659-113">屬性</span><span class="sxs-lookup"><span data-stu-id="28659-113">Attribute</span></span>|<span data-ttu-id="28659-114">描述</span><span class="sxs-lookup"><span data-stu-id="28659-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28659-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="28659-115">protectionLevel</span></span>|<span data-ttu-id="28659-116">定義訊息層級安全性。</span><span class="sxs-lookup"><span data-stu-id="28659-116">Defines message-level security.</span></span> <span data-ttu-id="28659-117">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="28659-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="28659-118">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="28659-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="28659-119">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="28659-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="28659-120">-None：沒有保護。</span><span class="sxs-lookup"><span data-stu-id="28659-120">-   None: No protection.</span></span><br /><span data-ttu-id="28659-121">-Sign：訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="28659-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="28659-122">-EncryptAndSign：訊息已簽署並加密。</span><span class="sxs-lookup"><span data-stu-id="28659-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="28659-123">預設為 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="28659-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="28659-124">此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="28659-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28659-125">子項目</span><span class="sxs-lookup"><span data-stu-id="28659-125">Child Elements</span></span>  
 <span data-ttu-id="28659-126">None</span><span class="sxs-lookup"><span data-stu-id="28659-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28659-127">父項目</span><span class="sxs-lookup"><span data-stu-id="28659-127">Parent Elements</span></span>  
  
|<span data-ttu-id="28659-128">項目</span><span class="sxs-lookup"><span data-stu-id="28659-128">Element</span></span>|<span data-ttu-id="28659-129">描述</span><span class="sxs-lookup"><span data-stu-id="28659-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28659-130">\<binding ></span><span class="sxs-lookup"><span data-stu-id="28659-130">\<binding></span></span>](bindings.md)|<span data-ttu-id="28659-131">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="28659-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28659-132">備註</span><span class="sxs-lookup"><span data-stu-id="28659-132">Remarks</span></span>  
 <span data-ttu-id="28659-133">TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。</span><span class="sxs-lookup"><span data-stu-id="28659-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="28659-134">具體來說，WCF 會提供安全性升級。</span><span class="sxs-lookup"><span data-stu-id="28659-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="28659-135">此傳輸安全性的設定是由這個 configuration 專案封裝，也是由[\<sslStreamSecurity >](sslstreamsecurity.md)（可以設定並新增至自訂系結）所封裝。</span><span class="sxs-lookup"><span data-stu-id="28659-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28659-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="28659-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="28659-137">繫結</span><span class="sxs-lookup"><span data-stu-id="28659-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="28659-138">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="28659-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="28659-139">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="28659-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="28659-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="28659-140">\<customBinding></span></span>](custombinding.md)
