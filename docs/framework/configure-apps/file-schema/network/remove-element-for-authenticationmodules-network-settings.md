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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154773"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="b1d2f-102">\<刪除>元素進行身份驗證模組（網路設置）</span><span class="sxs-lookup"><span data-stu-id="b1d2f-102">\<remove> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="b1d2f-103">從應用程式中刪除身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-103">Removes an authentication module from the application.</span></span>  

<span data-ttu-id="b1d2f-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1d2f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1d2f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1d2f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="b1d2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份驗證模組>**](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1d2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="b1d2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b1d2f-108">語法</span><span class="sxs-lookup"><span data-stu-id="b1d2f-108">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1d2f-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1d2f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1d2f-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1d2f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b1d2f-111">Attributes</span></span>  
  
|<span data-ttu-id="b1d2f-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-112">**Attribute**</span></span>|<span data-ttu-id="b1d2f-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="b1d2f-114">**型別**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-114">**type**</span></span>|<span data-ttu-id="b1d2f-115">要刪除的身份驗證模組的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-115">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1d2f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="b1d2f-116">Child Elements</span></span>  
 <span data-ttu-id="b1d2f-117">無。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1d2f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="b1d2f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b1d2f-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-119">**Element**</span></span>|<span data-ttu-id="b1d2f-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="b1d2f-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1d2f-121">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="b1d2f-121">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="b1d2f-122">指定用於驗證網路請求的模組。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-122">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1d2f-123">備註</span><span class="sxs-lookup"><span data-stu-id="b1d2f-123">Remarks</span></span>  
 <span data-ttu-id="b1d2f-124">該`remove`元素刪除在設定檔或配置層次結構中較高級別中定義的身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-124">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="b1d2f-125">`type`屬性的值應為有效的類名稱。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-125">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1d2f-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="b1d2f-126">Configuration Files</span></span>  
 <span data-ttu-id="b1d2f-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1d2f-128">範例</span><span class="sxs-lookup"><span data-stu-id="b1d2f-128">Example</span></span>  
 <span data-ttu-id="b1d2f-129">以下示例刪除身份驗證模組。</span><span class="sxs-lookup"><span data-stu-id="b1d2f-129">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1d2f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d2f-130">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="b1d2f-131">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="b1d2f-131">Network Settings Schema</span></span>](index.md)
