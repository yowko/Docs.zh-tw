---
title: <add> 的 <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398383"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="4cf4d-102">\<add> 的 \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="4cf4d-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="4cf4d-103">為裝載 WCF 服務的進程指定使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="4cf4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cf4d-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cf4d-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4cf4d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4cf4d-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cf4d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4cf4d-107">Attributes</span></span>  
  
|<span data-ttu-id="4cf4d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4cf4d-108">Attribute</span></span>|<span data-ttu-id="4cf4d-109">描述</span><span class="sxs-lookup"><span data-stu-id="4cf4d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4cf4d-110">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="4cf4d-110">securityIdentifier</span></span>|<span data-ttu-id="4cf4d-111">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-111">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="4cf4d-112">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-112">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cf4d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="4cf4d-113">Child Elements</span></span>  
 <span data-ttu-id="4cf4d-114">無。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cf4d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="4cf4d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4cf4d-116">元素</span><span class="sxs-lookup"><span data-stu-id="4cf4d-116">Element</span></span>|<span data-ttu-id="4cf4d-117">描述</span><span class="sxs-lookup"><span data-stu-id="4cf4d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="4cf4d-118">Configuration 專案的集合，其中包含 `securityIdentifier` 屬性，以指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-118">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4cf4d-119">範例</span><span class="sxs-lookup"><span data-stu-id="4cf4d-119">Example</span></span>  
 <span data-ttu-id="4cf4d-120">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="4cf4d-120">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cf4d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cf4d-121">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
