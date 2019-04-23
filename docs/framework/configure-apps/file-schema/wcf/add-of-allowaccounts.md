---
title: <add> 的 <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1c6764b37b2aa5349b8ccf63e6b7c2bc580b69b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186598"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="7bcfb-102">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="7bcfb-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="7bcfb-103">指定處理序裝載 WCF 服務，且已授權可連線共用服務的存取權的使用者的帳戶。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="7bcfb-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7bcfb-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bcfb-105">語法</span><span class="sxs-lookup"><span data-stu-id="7bcfb-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bcfb-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7bcfb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7bcfb-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bcfb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7bcfb-108">Attributes</span></span>  
  
|<span data-ttu-id="7bcfb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7bcfb-109">Attribute</span></span>|<span data-ttu-id="7bcfb-110">描述</span><span class="sxs-lookup"><span data-stu-id="7bcfb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bcfb-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7bcfb-111">securityIdentifier</span></span>|<span data-ttu-id="7bcfb-112">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="7bcfb-113">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bcfb-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7bcfb-114">Child Elements</span></span>  
 <span data-ttu-id="7bcfb-115">無。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bcfb-116">父項目</span><span class="sxs-lookup"><span data-stu-id="7bcfb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7bcfb-117">項目</span><span class="sxs-lookup"><span data-stu-id="7bcfb-117">Element</span></span>|<span data-ttu-id="7bcfb-118">描述</span><span class="sxs-lookup"><span data-stu-id="7bcfb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bcfb-119">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="7bcfb-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="7bcfb-120">包含的組態項目的集合`securityIdentifier`屬性來指定裝載 WCF 服務，且已授權可連線共用服務的存取權的處理程序的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7bcfb-121">範例</span><span class="sxs-lookup"><span data-stu-id="7bcfb-121">Example</span></span>  
 <span data-ttu-id="7bcfb-122">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="7bcfb-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7bcfb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bcfb-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
