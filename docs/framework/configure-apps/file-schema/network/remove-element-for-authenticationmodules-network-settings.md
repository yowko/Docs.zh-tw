---
title: authenticationModules 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: d171fea193bbae068e69b8976abb8e56a5623f02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154773"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="5677c-102">authenticationModules 的 \<remove> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5677c-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="5677c-103">從應用程式移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5677c-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5677c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5677c-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5677c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5677c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5677c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5677c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5677c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5677c-107">Attributes</span></span>  
  
|<span data-ttu-id="5677c-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5677c-108">**Attribute**</span></span>|<span data-ttu-id="5677c-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="5677c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="5677c-110">**type**</span><span class="sxs-lookup"><span data-stu-id="5677c-110">**type**</span></span>|<span data-ttu-id="5677c-111">要移除的驗證模組名稱。</span><span class="sxs-lookup"><span data-stu-id="5677c-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5677c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5677c-112">Child Elements</span></span>  
 <span data-ttu-id="5677c-113">無。</span><span class="sxs-lookup"><span data-stu-id="5677c-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5677c-114">父項目</span><span class="sxs-lookup"><span data-stu-id="5677c-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5677c-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="5677c-115">**Element**</span></span>|<span data-ttu-id="5677c-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="5677c-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5677c-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="5677c-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="5677c-118">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="5677c-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5677c-119">備註</span><span class="sxs-lookup"><span data-stu-id="5677c-119">Remarks</span></span>  
 <span data-ttu-id="5677c-120">`remove`元素會移除先前在設定檔或設定階層中較高層級定義的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5677c-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="5677c-121">屬性的值 `type` 應該是有效的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="5677c-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5677c-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="5677c-122">Configuration Files</span></span>  
 <span data-ttu-id="5677c-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="5677c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5677c-124">範例</span><span class="sxs-lookup"><span data-stu-id="5677c-124">Example</span></span>  
 <span data-ttu-id="5677c-125">下列範例會移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5677c-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5677c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5677c-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5677c-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5677c-127">Network Settings Schema</span></span>](index.md)
