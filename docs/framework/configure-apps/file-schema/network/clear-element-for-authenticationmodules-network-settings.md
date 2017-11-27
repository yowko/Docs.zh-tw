---
title: "&lt;清除&gt;authenticationModules （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f056894148177e6b540fd45569140a996b6b888f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="463ce-102">&lt;清除&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="463ce-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="463ce-103">清除所有的驗證模組，從應用程式。</span><span class="sxs-lookup"><span data-stu-id="463ce-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="463ce-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="463ce-104">\<configuration></span></span>  
<span data-ttu-id="463ce-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="463ce-105">\<system.net></span></span>  
<span data-ttu-id="463ce-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="463ce-106">\<authenticationModules></span></span>  
<span data-ttu-id="463ce-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="463ce-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463ce-108">語法</span><span class="sxs-lookup"><span data-stu-id="463ce-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="463ce-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="463ce-109">Attributes and Elements</span></span>  
 <span data-ttu-id="463ce-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="463ce-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="463ce-111">屬性</span><span class="sxs-lookup"><span data-stu-id="463ce-111">Attributes</span></span>  
 <span data-ttu-id="463ce-112">無。</span><span class="sxs-lookup"><span data-stu-id="463ce-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="463ce-113">子元素</span><span class="sxs-lookup"><span data-stu-id="463ce-113">Child Elements</span></span>  
 <span data-ttu-id="463ce-114">無。</span><span class="sxs-lookup"><span data-stu-id="463ce-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="463ce-115">父項目</span><span class="sxs-lookup"><span data-stu-id="463ce-115">Parent Elements</span></span>  
  
|<span data-ttu-id="463ce-116">**目**</span><span class="sxs-lookup"><span data-stu-id="463ce-116">**Element**</span></span>|<span data-ttu-id="463ce-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="463ce-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="463ce-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="463ce-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="463ce-119">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="463ce-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="463ce-120">備註</span><span class="sxs-lookup"><span data-stu-id="463ce-120">Remarks</span></span>  
 <span data-ttu-id="463ce-121">`clear`項目會移除所有先前已定義在組態檔中或在組態階層架構中較高層級的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="463ce-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="463ce-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="463ce-122">Configuration Files</span></span>  
 <span data-ttu-id="463ce-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="463ce-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="463ce-124">範例</span><span class="sxs-lookup"><span data-stu-id="463ce-124">Example</span></span>  
 <span data-ttu-id="463ce-125">下列範例會移除所有設定的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="463ce-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="463ce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="463ce-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="463ce-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="463ce-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
