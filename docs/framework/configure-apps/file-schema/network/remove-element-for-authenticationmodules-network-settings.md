---
title: "&lt;移除&gt;authenticationModules （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: eb8490241d4ec8a34a76aa6087c1f4d27d5cebb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6ba59-102">&lt;移除&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="6ba59-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="6ba59-103">移除應用程式中的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="6ba59-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="6ba59-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6ba59-104">\<configuration></span></span>  
<span data-ttu-id="6ba59-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="6ba59-105">\<system.net></span></span>  
<span data-ttu-id="6ba59-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="6ba59-106">\<authenticationModules></span></span>  
<span data-ttu-id="6ba59-107">\<移除 ></span><span class="sxs-lookup"><span data-stu-id="6ba59-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba59-108">語法</span><span class="sxs-lookup"><span data-stu-id="6ba59-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ba59-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ba59-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6ba59-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6ba59-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ba59-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6ba59-111">Attributes</span></span>  
  
|<span data-ttu-id="6ba59-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6ba59-112">**Attribute**</span></span>|<span data-ttu-id="6ba59-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="6ba59-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="6ba59-114">**type**</span><span class="sxs-lookup"><span data-stu-id="6ba59-114">**type**</span></span>|<span data-ttu-id="6ba59-115">若要移除的驗證模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ba59-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ba59-116">子元素</span><span class="sxs-lookup"><span data-stu-id="6ba59-116">Child Elements</span></span>  
 <span data-ttu-id="6ba59-117">無。</span><span class="sxs-lookup"><span data-stu-id="6ba59-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ba59-118">父項目</span><span class="sxs-lookup"><span data-stu-id="6ba59-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6ba59-119">**目**</span><span class="sxs-lookup"><span data-stu-id="6ba59-119">**Element**</span></span>|<span data-ttu-id="6ba59-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="6ba59-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6ba59-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6ba59-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="6ba59-122">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="6ba59-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ba59-123">備註</span><span class="sxs-lookup"><span data-stu-id="6ba59-123">Remarks</span></span>  
 <span data-ttu-id="6ba59-124">`remove`項目會移除先前已定義在組態檔中或在組態階層架構中較高層級的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="6ba59-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="6ba59-125">值`type`屬性應該是有效的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="6ba59-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6ba59-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="6ba59-126">Configuration Files</span></span>  
 <span data-ttu-id="6ba59-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="6ba59-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba59-128">範例</span><span class="sxs-lookup"><span data-stu-id="6ba59-128">Example</span></span>  
 <span data-ttu-id="6ba59-129">下列範例會移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="6ba59-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ba59-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ba59-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="6ba59-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6ba59-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
