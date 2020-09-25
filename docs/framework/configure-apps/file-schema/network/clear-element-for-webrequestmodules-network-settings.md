---
title: webRequestModules 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 892058dd8af8a38bd7bde868b34a2c6899d9a989
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184036"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="66fa1-102">webRequestModules 的 \<clear> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="66fa1-102">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="66fa1-103">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="66fa1-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="66fa1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="66fa1-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66fa1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66fa1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="66fa1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="66fa1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66fa1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="66fa1-107">Attributes</span></span>  

 <span data-ttu-id="66fa1-108">無。</span><span class="sxs-lookup"><span data-stu-id="66fa1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66fa1-109">子元素</span><span class="sxs-lookup"><span data-stu-id="66fa1-109">Child Elements</span></span>  

 <span data-ttu-id="66fa1-110">無。</span><span class="sxs-lookup"><span data-stu-id="66fa1-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66fa1-111">父項目</span><span class="sxs-lookup"><span data-stu-id="66fa1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="66fa1-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="66fa1-112">**Element**</span></span>|<span data-ttu-id="66fa1-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="66fa1-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="66fa1-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="66fa1-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="66fa1-115">指定用來向網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="66fa1-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66fa1-116">備註</span><span class="sxs-lookup"><span data-stu-id="66fa1-116">Remarks</span></span>  

 <span data-ttu-id="66fa1-117">專案 `clear` 會移除先前在設定檔中或在設定階層中較高層級定義的所有已註冊 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="66fa1-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="66fa1-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="66fa1-118">Configuration Files</span></span>  

 <span data-ttu-id="66fa1-119">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="66fa1-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66fa1-120">範例</span><span class="sxs-lookup"><span data-stu-id="66fa1-120">Example</span></span>  

 <span data-ttu-id="66fa1-121">下列範例會清除所有 Web 要求模組，然後註冊 HTTP 的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="66fa1-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66fa1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66fa1-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="66fa1-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="66fa1-123">Network Settings Schema</span></span>](index.md)
