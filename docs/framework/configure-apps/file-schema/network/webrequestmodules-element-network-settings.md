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
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697467"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="112e0-102">@no__t 0webRequestModules > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="112e0-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="112e0-103">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="112e0-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="112e0-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="112e0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="112e0-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="112e0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="112e0-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="112e0-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112e0-107">語法</span><span class="sxs-lookup"><span data-stu-id="112e0-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="112e0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="112e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="112e0-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="112e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="112e0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="112e0-110">Attributes</span></span>  
 <span data-ttu-id="112e0-111">無。</span><span class="sxs-lookup"><span data-stu-id="112e0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="112e0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="112e0-112">Child Elements</span></span>  
  
|<span data-ttu-id="112e0-113">**目**</span><span class="sxs-lookup"><span data-stu-id="112e0-113">**Element**</span></span>|<span data-ttu-id="112e0-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="112e0-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="112e0-115">add</span><span class="sxs-lookup"><span data-stu-id="112e0-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="112e0-116">將自訂 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="112e0-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="112e0-117">clear</span><span class="sxs-lookup"><span data-stu-id="112e0-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="112e0-118">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="112e0-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="112e0-119">remove</span><span class="sxs-lookup"><span data-stu-id="112e0-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="112e0-120">從應用程式中移除自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="112e0-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="112e0-121">父項目</span><span class="sxs-lookup"><span data-stu-id="112e0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="112e0-122">**目**</span><span class="sxs-lookup"><span data-stu-id="112e0-122">**Element**</span></span>|<span data-ttu-id="112e0-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="112e0-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="112e0-124">system.net</span><span class="sxs-lookup"><span data-stu-id="112e0-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="112e0-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="112e0-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="112e0-126">備註</span><span class="sxs-lookup"><span data-stu-id="112e0-126">Remarks</span></span>  
 <span data-ttu-id="112e0-127">`webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。</span><span class="sxs-lookup"><span data-stu-id="112e0-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="112e0-128">Web 要求模組必須執行 <xref:System.Net.IWebRequestCreate> 介面。</span><span class="sxs-lookup"><span data-stu-id="112e0-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="112e0-129">.NET Framework 包含以 `http://` 開頭的 Uri Web 要求模組，`https://` 和 `file://`。</span><span class="sxs-lookup"><span data-stu-id="112e0-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="112e0-130">您只能藉由在設定檔中註冊自訂模組來覆寫預設模組。</span><span class="sxs-lookup"><span data-stu-id="112e0-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="112e0-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="112e0-131">Configuration Files</span></span>  
 <span data-ttu-id="112e0-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="112e0-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="112e0-133">範例</span><span class="sxs-lookup"><span data-stu-id="112e0-133">Example</span></span>  
 <span data-ttu-id="112e0-134">下列範例會註冊預設的 HTTP 模組。</span><span class="sxs-lookup"><span data-stu-id="112e0-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="112e0-135">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="112e0-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="112e0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="112e0-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="112e0-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="112e0-137">Network Settings Schema</span></span>](index.md)
