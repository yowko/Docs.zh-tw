---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926604"
---
# <a name="allowaccounts"></a><span data-ttu-id="d8041-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="d8041-101">\<allowAccounts></span></span>
<span data-ttu-id="d8041-102">包含設定專案的集合, 這些專案會指定主控 Windows Communication Foundation (WCF) 服務之進程的使用者帳戶, 並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="d8041-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="d8041-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="d8041-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8041-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8041-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8041-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8041-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d8041-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8041-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8041-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d8041-107">Attributes</span></span>  
 <span data-ttu-id="d8041-108">無。</span><span class="sxs-lookup"><span data-stu-id="d8041-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8041-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d8041-109">Child Elements</span></span>  
  
|<span data-ttu-id="d8041-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d8041-110">Attribute</span></span>|<span data-ttu-id="d8041-111">描述</span><span class="sxs-lookup"><span data-stu-id="d8041-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d8041-112">\<add></span><span class="sxs-lookup"><span data-stu-id="d8041-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="d8041-113">加入裝載 WCF 服務之進程的使用者帳戶, 並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="d8041-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8041-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d8041-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d8041-115">項目</span><span class="sxs-lookup"><span data-stu-id="d8041-115">Element</span></span>|<span data-ttu-id="d8041-116">描述</span><span class="sxs-lookup"><span data-stu-id="d8041-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8041-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="d8041-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="d8041-118">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="d8041-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8041-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8041-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
