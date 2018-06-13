---
title: '&lt;allowAccounts&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349687"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="59dce-102">&lt;allowAccounts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="59dce-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="59dce-103">指定裝載 WCF 服務，且已授權可連線共用服務之處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="59dce-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="59dce-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="59dce-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59dce-105">語法</span><span class="sxs-lookup"><span data-stu-id="59dce-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59dce-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="59dce-106">Attributes and Elements</span></span>  
 <span data-ttu-id="59dce-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="59dce-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59dce-108">屬性</span><span class="sxs-lookup"><span data-stu-id="59dce-108">Attributes</span></span>  
  
|<span data-ttu-id="59dce-109">屬性</span><span class="sxs-lookup"><span data-stu-id="59dce-109">Attribute</span></span>|<span data-ttu-id="59dce-110">描述</span><span class="sxs-lookup"><span data-stu-id="59dce-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59dce-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="59dce-111">securityIdentifier</span></span>|<span data-ttu-id="59dce-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="59dce-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="59dce-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="59dce-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59dce-114">子項目</span><span class="sxs-lookup"><span data-stu-id="59dce-114">Child Elements</span></span>  
 <span data-ttu-id="59dce-115">無。</span><span class="sxs-lookup"><span data-stu-id="59dce-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59dce-116">父項目</span><span class="sxs-lookup"><span data-stu-id="59dce-116">Parent Elements</span></span>  
  
|<span data-ttu-id="59dce-117">項目</span><span class="sxs-lookup"><span data-stu-id="59dce-117">Element</span></span>|<span data-ttu-id="59dce-118">描述</span><span class="sxs-lookup"><span data-stu-id="59dce-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59dce-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="59dce-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="59dce-120">包含組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務之處理序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="59dce-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59dce-121">範例</span><span class="sxs-lookup"><span data-stu-id="59dce-121">Example</span></span>  
 <span data-ttu-id="59dce-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="59dce-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59dce-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59dce-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
