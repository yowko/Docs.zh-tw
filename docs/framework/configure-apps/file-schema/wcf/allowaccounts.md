---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102618"
---
# <a name="allowaccounts"></a><span data-ttu-id="17ea2-101">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="17ea2-101">\<allowAccounts></span></span>
<span data-ttu-id="17ea2-102">包含指定使用者帳戶的處理序裝載 Windows Communication Foundation (WCF) 服務和已授權可連線共用服務的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="17ea2-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="17ea2-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="17ea2-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ea2-104">語法</span><span class="sxs-lookup"><span data-stu-id="17ea2-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17ea2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17ea2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="17ea2-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="17ea2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17ea2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="17ea2-107">Attributes</span></span>  
 <span data-ttu-id="17ea2-108">無。</span><span class="sxs-lookup"><span data-stu-id="17ea2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17ea2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="17ea2-109">Child Elements</span></span>  
  
|<span data-ttu-id="17ea2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="17ea2-110">Attribute</span></span>|<span data-ttu-id="17ea2-111">描述</span><span class="sxs-lookup"><span data-stu-id="17ea2-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="17ea2-112">\<add></span><span class="sxs-lookup"><span data-stu-id="17ea2-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="17ea2-113">加入的使用者帳戶，以便裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序</span><span class="sxs-lookup"><span data-stu-id="17ea2-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17ea2-114">父項目</span><span class="sxs-lookup"><span data-stu-id="17ea2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="17ea2-115">項目</span><span class="sxs-lookup"><span data-stu-id="17ea2-115">Element</span></span>|<span data-ttu-id="17ea2-116">描述</span><span class="sxs-lookup"><span data-stu-id="17ea2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17ea2-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="17ea2-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="17ea2-118">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="17ea2-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17ea2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17ea2-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
