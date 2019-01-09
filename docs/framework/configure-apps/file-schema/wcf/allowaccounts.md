---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 61310d530cfec2862fb64155777cd0e88132f748
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145935"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="7427e-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="7427e-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="7427e-103">包含指定使用者帳戶的處理序裝載 Windows Communication Foundation (WCF) 服務和已授權可連線共用服務的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="7427e-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="7427e-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7427e-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7427e-105">語法</span><span class="sxs-lookup"><span data-stu-id="7427e-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7427e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7427e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7427e-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7427e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7427e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7427e-108">Attributes</span></span>  
 <span data-ttu-id="7427e-109">無。</span><span class="sxs-lookup"><span data-stu-id="7427e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7427e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7427e-110">Child Elements</span></span>  
  
|<span data-ttu-id="7427e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7427e-111">Attribute</span></span>|<span data-ttu-id="7427e-112">描述</span><span class="sxs-lookup"><span data-stu-id="7427e-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7427e-113">\<add></span><span class="sxs-lookup"><span data-stu-id="7427e-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="7427e-114">加入的使用者帳戶，以便裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序</span><span class="sxs-lookup"><span data-stu-id="7427e-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7427e-115">父項目</span><span class="sxs-lookup"><span data-stu-id="7427e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7427e-116">項目</span><span class="sxs-lookup"><span data-stu-id="7427e-116">Element</span></span>|<span data-ttu-id="7427e-117">描述</span><span class="sxs-lookup"><span data-stu-id="7427e-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7427e-118">[\<net.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md)或是[ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="7427e-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="7427e-119">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="7427e-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7427e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7427e-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
