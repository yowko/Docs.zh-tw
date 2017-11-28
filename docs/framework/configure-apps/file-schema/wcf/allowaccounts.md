---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8e1cf4c4428814361a56b5fd06dcce9e1512c836
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="e5e2c-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="e5e2c-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="e5e2c-103">包含組態項目的集合，這些項目指定裝載 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務之處理序的使用者帳戶，並被授予共用服務的連線存取權。</span><span class="sxs-lookup"><span data-stu-id="e5e2c-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="e5e2c-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="e5e2c-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e2c-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5e2c-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5e2c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5e2c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e5e2c-107">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e5e2c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5e2c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e5e2c-108">Attributes</span></span>  
 <span data-ttu-id="e5e2c-109">無。</span><span class="sxs-lookup"><span data-stu-id="e5e2c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5e2c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e5e2c-110">Child Elements</span></span>  
  
|<span data-ttu-id="e5e2c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e5e2c-111">Attribute</span></span>|<span data-ttu-id="e5e2c-112">說明</span><span class="sxs-lookup"><span data-stu-id="e5e2c-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e5e2c-113">\<add></span><span class="sxs-lookup"><span data-stu-id="e5e2c-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="e5e2c-114">加入裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務之處理序的使用者帳戶，並獲授予共用服務的連線權限。</span><span class="sxs-lookup"><span data-stu-id="e5e2c-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5e2c-115">父項目</span><span class="sxs-lookup"><span data-stu-id="e5e2c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e5e2c-116">項目</span><span class="sxs-lookup"><span data-stu-id="e5e2c-116">Element</span></span>|<span data-ttu-id="e5e2c-117">說明</span><span class="sxs-lookup"><span data-stu-id="e5e2c-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5e2c-118">[\<net.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md)或[ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="e5e2c-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="e5e2c-119">指定 Net Pipe 或 TCP 共用服務的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e5e2c-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5e2c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e2c-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
