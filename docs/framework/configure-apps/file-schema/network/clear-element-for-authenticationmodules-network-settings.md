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
ms.workload: dotnet
ms.openlocfilehash: b1c27ba6cdae88a36813dcf67ffc386c94403c1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="05cff-102">&lt;清除&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="05cff-102">&lt;clear&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="05cff-103">清除所有的驗證模組，從應用程式。</span><span class="sxs-lookup"><span data-stu-id="05cff-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="05cff-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="05cff-104">\<configuration></span></span>  
<span data-ttu-id="05cff-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="05cff-105">\<system.net></span></span>  
<span data-ttu-id="05cff-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="05cff-106">\<authenticationModules></span></span>  
<span data-ttu-id="05cff-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="05cff-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05cff-108">語法</span><span class="sxs-lookup"><span data-stu-id="05cff-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05cff-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05cff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="05cff-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="05cff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05cff-111">屬性</span><span class="sxs-lookup"><span data-stu-id="05cff-111">Attributes</span></span>  
 <span data-ttu-id="05cff-112">無。</span><span class="sxs-lookup"><span data-stu-id="05cff-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05cff-113">子元素</span><span class="sxs-lookup"><span data-stu-id="05cff-113">Child Elements</span></span>  
 <span data-ttu-id="05cff-114">無。</span><span class="sxs-lookup"><span data-stu-id="05cff-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05cff-115">父項目</span><span class="sxs-lookup"><span data-stu-id="05cff-115">Parent Elements</span></span>  
  
|<span data-ttu-id="05cff-116">**目**</span><span class="sxs-lookup"><span data-stu-id="05cff-116">**Element**</span></span>|<span data-ttu-id="05cff-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="05cff-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05cff-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="05cff-118">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="05cff-119">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="05cff-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05cff-120">備註</span><span class="sxs-lookup"><span data-stu-id="05cff-120">Remarks</span></span>  
 <span data-ttu-id="05cff-121">`clear`項目會移除所有先前已定義在組態檔中或在組態階層架構中較高層級的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="05cff-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05cff-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="05cff-122">Configuration Files</span></span>  
 <span data-ttu-id="05cff-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="05cff-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05cff-124">範例</span><span class="sxs-lookup"><span data-stu-id="05cff-124">Example</span></span>  
 <span data-ttu-id="05cff-125">下列範例會移除所有設定的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="05cff-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05cff-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="05cff-126">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="05cff-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="05cff-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
