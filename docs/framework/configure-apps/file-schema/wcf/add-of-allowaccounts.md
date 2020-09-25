---
title: <add> 的 <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: cd4b9fd02eee2de1d0e8be185ffb69c0eae1cd58
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181722"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="d85df-102">\<add> 的 \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="d85df-102">\<add> of \<allowAccounts></span></span>

<span data-ttu-id="d85df-103">指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連線存取權。</span><span class="sxs-lookup"><span data-stu-id="d85df-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d85df-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d85df-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d85df-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d85df-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d85df-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d85df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d85df-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d85df-107">Attributes</span></span>  
  
|<span data-ttu-id="d85df-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d85df-108">Attribute</span></span>|<span data-ttu-id="d85df-109">描述</span><span class="sxs-lookup"><span data-stu-id="d85df-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d85df-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="d85df-110">securityIdentifier</span></span>|<span data-ttu-id="d85df-111">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d85df-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="d85df-112">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="d85df-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d85df-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d85df-113">Child Elements</span></span>  

 <span data-ttu-id="d85df-114">無。</span><span class="sxs-lookup"><span data-stu-id="d85df-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d85df-115">父項目</span><span class="sxs-lookup"><span data-stu-id="d85df-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d85df-116">項目</span><span class="sxs-lookup"><span data-stu-id="d85df-116">Element</span></span>|<span data-ttu-id="d85df-117">描述</span><span class="sxs-lookup"><span data-stu-id="d85df-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="d85df-118">設定專案的集合，其中包含 `securityIdentifier` 屬性，可指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="d85df-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d85df-119">範例</span><span class="sxs-lookup"><span data-stu-id="d85df-119">Example</span></span>  

 <span data-ttu-id="d85df-120">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="d85df-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d85df-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d85df-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
