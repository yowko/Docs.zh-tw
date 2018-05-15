---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: bbfe0d5d531cf61c01f95d0e82ce0f894031d6f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="a6368-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="a6368-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="a6368-103">包含指定使用者處理序的帳戶裝載 Windows Communication Foundation (WCF) 服務且已授權可連線共用服務的組態項目的集合。</span><span class="sxs-lookup"><span data-stu-id="a6368-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="a6368-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="a6368-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6368-105">語法</span><span class="sxs-lookup"><span data-stu-id="a6368-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6368-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a6368-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a6368-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a6368-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6368-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a6368-108">Attributes</span></span>  
 <span data-ttu-id="a6368-109">無。</span><span class="sxs-lookup"><span data-stu-id="a6368-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6368-110">子項目</span><span class="sxs-lookup"><span data-stu-id="a6368-110">Child Elements</span></span>  
  
|<span data-ttu-id="a6368-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a6368-111">Attribute</span></span>|<span data-ttu-id="a6368-112">描述</span><span class="sxs-lookup"><span data-stu-id="a6368-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a6368-113">\<add></span><span class="sxs-lookup"><span data-stu-id="a6368-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="a6368-114">加入裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務之處理序的使用者帳戶，並獲授予共用服務的連線權限。</span><span class="sxs-lookup"><span data-stu-id="a6368-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6368-115">父項目</span><span class="sxs-lookup"><span data-stu-id="a6368-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a6368-116">項目</span><span class="sxs-lookup"><span data-stu-id="a6368-116">Element</span></span>|<span data-ttu-id="a6368-117">描述</span><span class="sxs-lookup"><span data-stu-id="a6368-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6368-118">[\<net.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md)或[ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="a6368-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="a6368-119">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="a6368-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6368-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6368-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
