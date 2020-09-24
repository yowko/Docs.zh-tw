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
ms.openlocfilehash: 6ac2287ba9b17727835d43a3e3b8876f210fb5c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167323"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="d9810-102">authenticationModules 的 \<clear> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d9810-102">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="d9810-103">從應用程式清除所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="d9810-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="d9810-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9810-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9810-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9810-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d9810-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d9810-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9810-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d9810-107">Attributes</span></span>  

 <span data-ttu-id="d9810-108">無。</span><span class="sxs-lookup"><span data-stu-id="d9810-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9810-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d9810-109">Child Elements</span></span>  

 <span data-ttu-id="d9810-110">無。</span><span class="sxs-lookup"><span data-stu-id="d9810-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9810-111">父項目</span><span class="sxs-lookup"><span data-stu-id="d9810-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d9810-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="d9810-112">**Element**</span></span>|<span data-ttu-id="d9810-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="d9810-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d9810-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="d9810-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="d9810-115">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="d9810-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9810-116">備註</span><span class="sxs-lookup"><span data-stu-id="d9810-116">Remarks</span></span>  

 <span data-ttu-id="d9810-117">專案 `clear` 會移除先前在設定檔或設定階層中較高層級定義的所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="d9810-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d9810-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="d9810-118">Configuration Files</span></span>  

 <span data-ttu-id="d9810-119">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d9810-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9810-120">範例</span><span class="sxs-lookup"><span data-stu-id="d9810-120">Example</span></span>  

 <span data-ttu-id="d9810-121">下列範例會移除所有已設定的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="d9810-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9810-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9810-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d9810-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d9810-123">Network Settings Schema</span></span>](index.md)
