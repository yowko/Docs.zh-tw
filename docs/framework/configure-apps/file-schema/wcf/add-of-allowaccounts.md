---
title: <add> 的 <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1ed0b5025ab969c45d7440f2a209426c5c87f549
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920281"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="3caf2-102">\<新增 d > \<的 ></span><span class="sxs-lookup"><span data-stu-id="3caf2-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="3caf2-103">為裝載 WCF 服務的進程指定使用者帳戶, 並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="3caf2-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="3caf2-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="3caf2-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3caf2-105">語法</span><span class="sxs-lookup"><span data-stu-id="3caf2-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3caf2-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3caf2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3caf2-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3caf2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3caf2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3caf2-108">Attributes</span></span>  
  
|<span data-ttu-id="3caf2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="3caf2-109">Attribute</span></span>|<span data-ttu-id="3caf2-110">描述</span><span class="sxs-lookup"><span data-stu-id="3caf2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3caf2-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="3caf2-111">securityIdentifier</span></span>|<span data-ttu-id="3caf2-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="3caf2-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="3caf2-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="3caf2-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3caf2-114">子元素</span><span class="sxs-lookup"><span data-stu-id="3caf2-114">Child Elements</span></span>  
 <span data-ttu-id="3caf2-115">無。</span><span class="sxs-lookup"><span data-stu-id="3caf2-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3caf2-116">父項目</span><span class="sxs-lookup"><span data-stu-id="3caf2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3caf2-117">項目</span><span class="sxs-lookup"><span data-stu-id="3caf2-117">Element</span></span>|<span data-ttu-id="3caf2-118">描述</span><span class="sxs-lookup"><span data-stu-id="3caf2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3caf2-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="3caf2-119">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="3caf2-120">Configuration 專案的集合, 其中包含`securityIdentifier`屬性, 以指定裝載 WCF 服務之進程的使用者帳戶, 並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="3caf2-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3caf2-121">範例</span><span class="sxs-lookup"><span data-stu-id="3caf2-121">Example</span></span>  
 <span data-ttu-id="3caf2-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="3caf2-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="3caf2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3caf2-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
