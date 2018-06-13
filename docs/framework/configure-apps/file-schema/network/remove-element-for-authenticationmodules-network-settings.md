---
title: '&lt;移除&gt;authenticationModules （網路設定） 的項目'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a22ddbada0162ba38589b244cab9123f33d7cf45
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742386"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="5cd5e-102">&lt;移除&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="5cd5e-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="5cd5e-103">移除應用程式中的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="5cd5e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5cd5e-104">\<configuration></span></span>  
<span data-ttu-id="5cd5e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5cd5e-105">\<system.net></span></span>  
<span data-ttu-id="5cd5e-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="5cd5e-106">\<authenticationModules></span></span>  
<span data-ttu-id="5cd5e-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="5cd5e-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd5e-108">語法</span><span class="sxs-lookup"><span data-stu-id="5cd5e-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cd5e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5cd5e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5cd5e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cd5e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5cd5e-111">Attributes</span></span>  
  
|<span data-ttu-id="5cd5e-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5cd5e-112">**Attribute**</span></span>|<span data-ttu-id="5cd5e-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="5cd5e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="5cd5e-114">**type**</span><span class="sxs-lookup"><span data-stu-id="5cd5e-114">**type**</span></span>|<span data-ttu-id="5cd5e-115">若要移除的驗證模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cd5e-116">子項目</span><span class="sxs-lookup"><span data-stu-id="5cd5e-116">Child Elements</span></span>  
 <span data-ttu-id="5cd5e-117">無。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cd5e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5cd5e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5cd5e-119">**目**</span><span class="sxs-lookup"><span data-stu-id="5cd5e-119">**Element**</span></span>|<span data-ttu-id="5cd5e-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="5cd5e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5cd5e-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="5cd5e-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="5cd5e-122">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cd5e-123">備註</span><span class="sxs-lookup"><span data-stu-id="5cd5e-123">Remarks</span></span>  
 <span data-ttu-id="5cd5e-124">`remove`項目會移除先前已定義在組態檔中或在組態階層架構中較高層級的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="5cd5e-125">值`type`屬性應該是有效的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5cd5e-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="5cd5e-126">Configuration Files</span></span>  
 <span data-ttu-id="5cd5e-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd5e-128">範例</span><span class="sxs-lookup"><span data-stu-id="5cd5e-128">Example</span></span>  
 <span data-ttu-id="5cd5e-129">下列範例會移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="5cd5e-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cd5e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cd5e-130">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="5cd5e-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5cd5e-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
