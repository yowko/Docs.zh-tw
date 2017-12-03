---
title: "&lt;allowAccounts&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="57919-102">&lt;allowAccounts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="57919-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="57919-103">指定裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務並獲得共用服務連線存取權之處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="57919-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="57919-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="57919-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57919-105">語法</span><span class="sxs-lookup"><span data-stu-id="57919-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57919-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57919-106">Attributes and Elements</span></span>  
 <span data-ttu-id="57919-107">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="57919-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57919-108">屬性</span><span class="sxs-lookup"><span data-stu-id="57919-108">Attributes</span></span>  
  
|<span data-ttu-id="57919-109">屬性</span><span class="sxs-lookup"><span data-stu-id="57919-109">Attribute</span></span>|<span data-ttu-id="57919-110">描述</span><span class="sxs-lookup"><span data-stu-id="57919-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="57919-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="57919-111">securityIdentifier</span></span>|<span data-ttu-id="57919-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="57919-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="57919-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="57919-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57919-114">子元素</span><span class="sxs-lookup"><span data-stu-id="57919-114">Child Elements</span></span>  
 <span data-ttu-id="57919-115">無。</span><span class="sxs-lookup"><span data-stu-id="57919-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57919-116">父項目</span><span class="sxs-lookup"><span data-stu-id="57919-116">Parent Elements</span></span>  
  
|<span data-ttu-id="57919-117">項目</span><span class="sxs-lookup"><span data-stu-id="57919-117">Element</span></span>|<span data-ttu-id="57919-118">說明</span><span class="sxs-lookup"><span data-stu-id="57919-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57919-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="57919-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="57919-120">組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="57919-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="57919-121">範例</span><span class="sxs-lookup"><span data-stu-id="57919-121">Example</span></span>  
 <span data-ttu-id="57919-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="57919-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57919-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57919-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
