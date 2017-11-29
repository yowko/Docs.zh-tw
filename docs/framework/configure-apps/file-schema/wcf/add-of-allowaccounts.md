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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 964e1ebc3dfc39a06b82dd1b6438e34642635393
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="53f4c-102">&lt;allowAccounts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="53f4c-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="53f4c-103">指定裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務並獲得共用服務連線存取權之處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="53f4c-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="53f4c-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="53f4c-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f4c-105">語法</span><span class="sxs-lookup"><span data-stu-id="53f4c-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53f4c-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53f4c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="53f4c-107">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="53f4c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53f4c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="53f4c-108">Attributes</span></span>  
  
|<span data-ttu-id="53f4c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="53f4c-109">Attribute</span></span>|<span data-ttu-id="53f4c-110">描述</span><span class="sxs-lookup"><span data-stu-id="53f4c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53f4c-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="53f4c-111">securityIdentifier</span></span>|<span data-ttu-id="53f4c-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="53f4c-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="53f4c-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="53f4c-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53f4c-114">子元素</span><span class="sxs-lookup"><span data-stu-id="53f4c-114">Child Elements</span></span>  
 <span data-ttu-id="53f4c-115">無。</span><span class="sxs-lookup"><span data-stu-id="53f4c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53f4c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="53f4c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="53f4c-117">項目</span><span class="sxs-lookup"><span data-stu-id="53f4c-117">Element</span></span>|<span data-ttu-id="53f4c-118">說明</span><span class="sxs-lookup"><span data-stu-id="53f4c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53f4c-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="53f4c-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="53f4c-120">組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="53f4c-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53f4c-121">範例</span><span class="sxs-lookup"><span data-stu-id="53f4c-121">Example</span></span>  
 <span data-ttu-id="53f4c-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="53f4c-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53f4c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53f4c-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
