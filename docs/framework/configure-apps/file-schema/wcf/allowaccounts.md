---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508410"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="0fc9a-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="0fc9a-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="0fc9a-103">包含指定使用者帳戶的處理序裝載 Windows Communication Foundation (WCF) 服務和已授權可連線共用服務的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="0fc9a-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="0fc9a-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0fc9a-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc9a-105">語法</span><span class="sxs-lookup"><span data-stu-id="0fc9a-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc9a-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0fc9a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0fc9a-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0fc9a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc9a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0fc9a-108">Attributes</span></span>  
 <span data-ttu-id="0fc9a-109">無。</span><span class="sxs-lookup"><span data-stu-id="0fc9a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fc9a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0fc9a-110">Child Elements</span></span>  
  
|<span data-ttu-id="0fc9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0fc9a-111">Attribute</span></span>|<span data-ttu-id="0fc9a-112">描述</span><span class="sxs-lookup"><span data-stu-id="0fc9a-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="0fc9a-113">\<add></span><span class="sxs-lookup"><span data-stu-id="0fc9a-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="0fc9a-114">加入的使用者帳戶，以便裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序</span><span class="sxs-lookup"><span data-stu-id="0fc9a-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc9a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="0fc9a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc9a-116">項目</span><span class="sxs-lookup"><span data-stu-id="0fc9a-116">Element</span></span>|<span data-ttu-id="0fc9a-117">描述</span><span class="sxs-lookup"><span data-stu-id="0fc9a-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fc9a-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="0fc9a-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="0fc9a-119">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="0fc9a-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fc9a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc9a-120">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
