---
title: '&lt;allowAccounts&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 20e1052a0517bb170cf796dd40d58c298185a958
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="76db3-102">&lt;allowAccounts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="76db3-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="76db3-103">指定裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務並獲得共用服務連線存取權之處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="76db3-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="76db3-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="76db3-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76db3-105">語法</span><span class="sxs-lookup"><span data-stu-id="76db3-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76db3-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76db3-106">Attributes and Elements</span></span>  
 <span data-ttu-id="76db3-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="76db3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76db3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="76db3-108">Attributes</span></span>  
  
|<span data-ttu-id="76db3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="76db3-109">Attribute</span></span>|<span data-ttu-id="76db3-110">描述</span><span class="sxs-lookup"><span data-stu-id="76db3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76db3-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="76db3-111">securityIdentifier</span></span>|<span data-ttu-id="76db3-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="76db3-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="76db3-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="76db3-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76db3-114">子項目</span><span class="sxs-lookup"><span data-stu-id="76db3-114">Child Elements</span></span>  
 <span data-ttu-id="76db3-115">無。</span><span class="sxs-lookup"><span data-stu-id="76db3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76db3-116">父項目</span><span class="sxs-lookup"><span data-stu-id="76db3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="76db3-117">項目</span><span class="sxs-lookup"><span data-stu-id="76db3-117">Element</span></span>|<span data-ttu-id="76db3-118">描述</span><span class="sxs-lookup"><span data-stu-id="76db3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76db3-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="76db3-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="76db3-120">組態項目的集合，其中包含 `securityIdentifier` 屬性，此屬性可為裝載 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務且已授權可連線共用服務的處理序指定使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="76db3-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76db3-121">範例</span><span class="sxs-lookup"><span data-stu-id="76db3-121">Example</span></span>  
 <span data-ttu-id="76db3-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="76db3-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76db3-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76db3-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
