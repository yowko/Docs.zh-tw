---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398410"
---
# <a name="allowaccounts"></a><span data-ttu-id="8312e-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="8312e-101">\<allowAccounts></span></span>
<span data-ttu-id="8312e-102">包含設定專案的集合，這些專案會指定主控 Windows Communication Foundation （WCF）服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="8312e-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="8312e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8312e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8312e-104">&nbsp;&nbsp;[ **\<System.servicemodel. 啟用 >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="8312e-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="8312e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net.pipe >** ](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="8312e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="8312e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<d >**</span><span class="sxs-lookup"><span data-stu-id="8312e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8312e-107">語法</span><span class="sxs-lookup"><span data-stu-id="8312e-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8312e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8312e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8312e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8312e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8312e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8312e-110">Attributes</span></span>  
 <span data-ttu-id="8312e-111">無。</span><span class="sxs-lookup"><span data-stu-id="8312e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8312e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8312e-112">Child Elements</span></span>  
  
|<span data-ttu-id="8312e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8312e-113">Attribute</span></span>|<span data-ttu-id="8312e-114">描述</span><span class="sxs-lookup"><span data-stu-id="8312e-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8312e-115">\<add></span><span class="sxs-lookup"><span data-stu-id="8312e-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="8312e-116">加入裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="8312e-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8312e-117">父項目</span><span class="sxs-lookup"><span data-stu-id="8312e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8312e-118">項目</span><span class="sxs-lookup"><span data-stu-id="8312e-118">Element</span></span>|<span data-ttu-id="8312e-119">描述</span><span class="sxs-lookup"><span data-stu-id="8312e-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8312e-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="8312e-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="8312e-121">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="8312e-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8312e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8312e-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
