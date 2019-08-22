---
title: authenticationModules 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: 12ac146926103b40073d34f48895b0645c8a8ed2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659471"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ebf43-102">\<清除 Authenticationmodules 專案的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="ebf43-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="ebf43-103">清除應用程式中的所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="ebf43-103">Clears all authentication modules from the application.</span></span>  
  
 <span data-ttu-id="ebf43-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ebf43-104">\<configuration></span></span>  
<span data-ttu-id="ebf43-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ebf43-105">\<system.net></span></span>  
<span data-ttu-id="ebf43-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="ebf43-106">\<authenticationModules></span></span>  
<span data-ttu-id="ebf43-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="ebf43-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf43-108">語法</span><span class="sxs-lookup"><span data-stu-id="ebf43-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebf43-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ebf43-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ebf43-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ebf43-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebf43-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ebf43-111">Attributes</span></span>  
 <span data-ttu-id="ebf43-112">無。</span><span class="sxs-lookup"><span data-stu-id="ebf43-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ebf43-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ebf43-113">Child Elements</span></span>  
 <span data-ttu-id="ebf43-114">無。</span><span class="sxs-lookup"><span data-stu-id="ebf43-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebf43-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ebf43-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ebf43-116">**目**</span><span class="sxs-lookup"><span data-stu-id="ebf43-116">**Element**</span></span>|<span data-ttu-id="ebf43-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="ebf43-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ebf43-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ebf43-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="ebf43-119">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="ebf43-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf43-120">備註</span><span class="sxs-lookup"><span data-stu-id="ebf43-120">Remarks</span></span>  
 <span data-ttu-id="ebf43-121">`clear`元素會移除先前在設定檔或設定階層中較高層級定義的所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="ebf43-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ebf43-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="ebf43-122">Configuration Files</span></span>  
 <span data-ttu-id="ebf43-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ebf43-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebf43-124">範例</span><span class="sxs-lookup"><span data-stu-id="ebf43-124">Example</span></span>  
 <span data-ttu-id="ebf43-125">下列範例會移除所有已設定的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="ebf43-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebf43-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf43-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ebf43-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ebf43-127">Network Settings Schema</span></span>](index.md)
