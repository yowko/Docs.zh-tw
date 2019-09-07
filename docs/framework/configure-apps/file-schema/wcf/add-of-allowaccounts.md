---
title: <add> 的 <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398383"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="2d502-102">\<新增 d > \<的 ></span><span class="sxs-lookup"><span data-stu-id="2d502-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="2d502-103">為裝載 WCF 服務的進程指定使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="2d502-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="2d502-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d502-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d502-105">&nbsp;&nbsp;[ **\<System.servicemodel. 啟用 >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="2d502-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="2d502-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net.pipe >** ](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="2d502-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="2d502-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<d >** ](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="2d502-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="2d502-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="2d502-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d502-109">語法</span><span class="sxs-lookup"><span data-stu-id="2d502-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d502-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2d502-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2d502-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2d502-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d502-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2d502-112">Attributes</span></span>  
  
|<span data-ttu-id="2d502-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2d502-113">Attribute</span></span>|<span data-ttu-id="2d502-114">說明</span><span class="sxs-lookup"><span data-stu-id="2d502-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d502-115">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2d502-115">securityIdentifier</span></span>|<span data-ttu-id="2d502-116">字串，指定用於識別使用者帳戶的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2d502-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="2d502-117">預設值為 LocalSystem、Administrators、NS、LS 和 IIS_USRS。</span><span class="sxs-lookup"><span data-stu-id="2d502-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d502-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2d502-118">Child Elements</span></span>  
 <span data-ttu-id="2d502-119">無。</span><span class="sxs-lookup"><span data-stu-id="2d502-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d502-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2d502-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2d502-121">項目</span><span class="sxs-lookup"><span data-stu-id="2d502-121">Element</span></span>|<span data-ttu-id="2d502-122">描述</span><span class="sxs-lookup"><span data-stu-id="2d502-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d502-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="2d502-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="2d502-124">Configuration 專案的集合，其中包含`securityIdentifier`屬性，以指定裝載 WCF 服務之進程的使用者帳戶，並授與共享服務的連接存取權。</span><span class="sxs-lookup"><span data-stu-id="2d502-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2d502-125">範例</span><span class="sxs-lookup"><span data-stu-id="2d502-125">Example</span></span>  
 <span data-ttu-id="2d502-126">下列組態範例會新增使用者帳戶的五個預設識別項到此集合中。</span><span class="sxs-lookup"><span data-stu-id="2d502-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d502-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d502-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
