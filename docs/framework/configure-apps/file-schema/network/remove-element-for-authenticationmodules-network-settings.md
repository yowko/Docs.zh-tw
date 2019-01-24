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
ms.openlocfilehash: 20d90c4554f9718651070456f6d4a14475d88bf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651574"
---
# <a name="ltremovegt-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="dcb6f-102">&lt;移除&gt;authenticationModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="dcb6f-102">&lt;remove&gt; Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="dcb6f-103">移除應用程式中的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-103">Removes an authentication module from the application.</span></span>  
  
 <span data-ttu-id="dcb6f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dcb6f-104">\<configuration></span></span>  
<span data-ttu-id="dcb6f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dcb6f-105">\<system.net></span></span>  
<span data-ttu-id="dcb6f-106">\<authenticationModules></span><span class="sxs-lookup"><span data-stu-id="dcb6f-106">\<authenticationModules></span></span>  
<span data-ttu-id="dcb6f-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="dcb6f-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb6f-108">語法</span><span class="sxs-lookup"><span data-stu-id="dcb6f-108">Syntax</span></span>  
  
```xml  
<remove   
   type="authentication module name"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcb6f-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dcb6f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dcb6f-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcb6f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dcb6f-111">Attributes</span></span>  
  
|<span data-ttu-id="dcb6f-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="dcb6f-112">**Attribute**</span></span>|<span data-ttu-id="dcb6f-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="dcb6f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="dcb6f-114">**type**</span><span class="sxs-lookup"><span data-stu-id="dcb6f-114">**type**</span></span>|<span data-ttu-id="dcb6f-115">若要移除的驗證模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcb6f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="dcb6f-116">Child Elements</span></span>  
 <span data-ttu-id="dcb6f-117">無。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcb6f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="dcb6f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dcb6f-119">**目**</span><span class="sxs-lookup"><span data-stu-id="dcb6f-119">**Element**</span></span>|<span data-ttu-id="dcb6f-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="dcb6f-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dcb6f-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="dcb6f-121">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="dcb6f-122">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb6f-123">備註</span><span class="sxs-lookup"><span data-stu-id="dcb6f-123">Remarks</span></span>  
 <span data-ttu-id="dcb6f-124">`remove`項目移除先前已定義在組態檔中或在組態階層架構中較高層級的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="dcb6f-125">值`type`屬性應該是有效的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dcb6f-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="dcb6f-126">Configuration Files</span></span>  
 <span data-ttu-id="dcb6f-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcb6f-128">範例</span><span class="sxs-lookup"><span data-stu-id="dcb6f-128">Example</span></span>  
 <span data-ttu-id="dcb6f-129">下列範例會移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="dcb6f-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcb6f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcb6f-130">See also</span></span>
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="dcb6f-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="dcb6f-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
