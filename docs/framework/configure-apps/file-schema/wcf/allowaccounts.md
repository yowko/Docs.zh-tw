---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398410"
---
# \<allowAccounts>
<span data-ttu-id="02140-101">包含設定專案的集合，這些專案會指定主控 Windows Communication Foundation （WCF）服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="02140-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="02140-102">語法</span><span class="sxs-lookup"><span data-stu-id="02140-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02140-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02140-103">Attributes and Elements</span></span>  
 <span data-ttu-id="02140-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="02140-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02140-105">屬性</span><span class="sxs-lookup"><span data-stu-id="02140-105">Attributes</span></span>  
 <span data-ttu-id="02140-106">無。</span><span class="sxs-lookup"><span data-stu-id="02140-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02140-107">子元素</span><span class="sxs-lookup"><span data-stu-id="02140-107">Child Elements</span></span>  
  
|<span data-ttu-id="02140-108">屬性</span><span class="sxs-lookup"><span data-stu-id="02140-108">Attribute</span></span>|<span data-ttu-id="02140-109">描述</span><span class="sxs-lookup"><span data-stu-id="02140-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="02140-110">加入裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="02140-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02140-111">父項目</span><span class="sxs-lookup"><span data-stu-id="02140-111">Parent Elements</span></span>  
  
|<span data-ttu-id="02140-112">元素</span><span class="sxs-lookup"><span data-stu-id="02140-112">Element</span></span>|<span data-ttu-id="02140-113">描述</span><span class="sxs-lookup"><span data-stu-id="02140-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02140-114">[\<net.pipe>](net-pipe.md)或[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="02140-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="02140-115">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="02140-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02140-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02140-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
