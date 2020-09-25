---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201638"
---
# \<allowAccounts>

<span data-ttu-id="8f733-101">包含設定專案的集合，這些專案會為裝載 Windows Communication Foundation (WCF) 服務的進程指定使用者帳戶，並授與共享服務的連線存取權。</span><span class="sxs-lookup"><span data-stu-id="8f733-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="8f733-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f733-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f733-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f733-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8f733-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8f733-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f733-105">屬性</span><span class="sxs-lookup"><span data-stu-id="8f733-105">Attributes</span></span>  

 <span data-ttu-id="8f733-106">無。</span><span class="sxs-lookup"><span data-stu-id="8f733-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f733-107">子元素</span><span class="sxs-lookup"><span data-stu-id="8f733-107">Child Elements</span></span>  
  
|<span data-ttu-id="8f733-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8f733-108">Attribute</span></span>|<span data-ttu-id="8f733-109">描述</span><span class="sxs-lookup"><span data-stu-id="8f733-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="8f733-110">為裝載 WCF 服務的進程加入使用者帳戶，並授與共享服務的連線存取權。</span><span class="sxs-lookup"><span data-stu-id="8f733-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f733-111">父項目</span><span class="sxs-lookup"><span data-stu-id="8f733-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8f733-112">項目</span><span class="sxs-lookup"><span data-stu-id="8f733-112">Element</span></span>|<span data-ttu-id="8f733-113">描述</span><span class="sxs-lookup"><span data-stu-id="8f733-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f733-114">[\<net.pipe>](net-pipe.md) 或 [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="8f733-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="8f733-115">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="8f733-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f733-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f733-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
