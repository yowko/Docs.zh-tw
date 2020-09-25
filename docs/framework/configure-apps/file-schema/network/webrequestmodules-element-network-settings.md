---
title: <webRequestModules> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 9396ca393523dce5593531f332e5c07241987947
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187000"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="355c8-102">\<webRequestModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="355c8-102">\<webRequestModules> Element (Network Settings)</span></span>

<span data-ttu-id="355c8-103">指定用來向網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="355c8-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="355c8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="355c8-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="355c8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="355c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="355c8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="355c8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="355c8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="355c8-107">Attributes</span></span>  

 <span data-ttu-id="355c8-108">無。</span><span class="sxs-lookup"><span data-stu-id="355c8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="355c8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="355c8-109">Child Elements</span></span>  
  
|<span data-ttu-id="355c8-110">**Element**</span><span class="sxs-lookup"><span data-stu-id="355c8-110">**Element**</span></span>|<span data-ttu-id="355c8-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="355c8-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="355c8-112">add</span><span class="sxs-lookup"><span data-stu-id="355c8-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="355c8-113">將自訂 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="355c8-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="355c8-114">清除</span><span class="sxs-lookup"><span data-stu-id="355c8-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="355c8-115">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="355c8-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="355c8-116">remove</span><span class="sxs-lookup"><span data-stu-id="355c8-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="355c8-117">從應用程式移除自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="355c8-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="355c8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="355c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="355c8-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="355c8-119">**Element**</span></span>|<span data-ttu-id="355c8-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="355c8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="355c8-121">system.net</span><span class="sxs-lookup"><span data-stu-id="355c8-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="355c8-122">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="355c8-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="355c8-123">備註</span><span class="sxs-lookup"><span data-stu-id="355c8-123">Remarks</span></span>  

 <span data-ttu-id="355c8-124">`webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。</span><span class="sxs-lookup"><span data-stu-id="355c8-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="355c8-125">Web 要求模組必須執行 <xref:System.Net.IWebRequestCreate> 介面。</span><span class="sxs-lookup"><span data-stu-id="355c8-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="355c8-126">.NET Framework 包含以、和開頭之 Uri 的 Web 要求 `http://` 模組 `https://` `file://` 。</span><span class="sxs-lookup"><span data-stu-id="355c8-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="355c8-127">您只能藉由在設定檔中註冊自訂模組來覆寫預設模組。</span><span class="sxs-lookup"><span data-stu-id="355c8-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="355c8-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="355c8-128">Configuration Files</span></span>  

 <span data-ttu-id="355c8-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="355c8-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="355c8-130">範例</span><span class="sxs-lookup"><span data-stu-id="355c8-130">Example</span></span>  

 <span data-ttu-id="355c8-131">下列範例會註冊預設的 HTTP 模組。</span><span class="sxs-lookup"><span data-stu-id="355c8-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="355c8-132">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="355c8-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="355c8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="355c8-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="355c8-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="355c8-134">Network Settings Schema</span></span>](index.md)
