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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154539"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="21669-102">\<webRequestModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="21669-102">\<webRequestModules> Element (Network Settings)</span></span>
<span data-ttu-id="21669-103">指定用於從網路主機請求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="21669-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[<span data-ttu-id="21669-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="21669-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="21669-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="21669-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="21669-106">&nbsp;&nbsp;&nbsp;&nbsp;\<web 請求模組></span><span class="sxs-lookup"><span data-stu-id="21669-106">&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21669-107">語法</span><span class="sxs-lookup"><span data-stu-id="21669-107">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21669-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="21669-108">Attributes and Elements</span></span>  
 <span data-ttu-id="21669-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="21669-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21669-110">屬性</span><span class="sxs-lookup"><span data-stu-id="21669-110">Attributes</span></span>  
 <span data-ttu-id="21669-111">無。</span><span class="sxs-lookup"><span data-stu-id="21669-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21669-112">子元素</span><span class="sxs-lookup"><span data-stu-id="21669-112">Child Elements</span></span>  
  
|<span data-ttu-id="21669-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="21669-113">**Element**</span></span>|<span data-ttu-id="21669-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="21669-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="21669-115">新增</span><span class="sxs-lookup"><span data-stu-id="21669-115">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="21669-116">向應用程式添加自訂 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="21669-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="21669-117">清楚</span><span class="sxs-lookup"><span data-stu-id="21669-117">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="21669-118">從應用程式中刪除所有已註冊的 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="21669-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="21669-119">移除</span><span class="sxs-lookup"><span data-stu-id="21669-119">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="21669-120">從應用程式中刪除自訂 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="21669-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21669-121">父項目</span><span class="sxs-lookup"><span data-stu-id="21669-121">Parent Elements</span></span>  
  
|<span data-ttu-id="21669-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="21669-122">**Element**</span></span>|<span data-ttu-id="21669-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="21669-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="21669-124">system.net</span><span class="sxs-lookup"><span data-stu-id="21669-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="21669-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="21669-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21669-126">備註</span><span class="sxs-lookup"><span data-stu-id="21669-126">Remarks</span></span>  
 <span data-ttu-id="21669-127">`webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。</span><span class="sxs-lookup"><span data-stu-id="21669-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="21669-128">Web 請求模組必須實現<xref:System.Net.IWebRequestCreate>介面。</span><span class="sxs-lookup"><span data-stu-id="21669-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="21669-129">.NET 框架包括以`http://`和`https://`開頭的 URI 的 Web`file://`請求模組。</span><span class="sxs-lookup"><span data-stu-id="21669-129">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="21669-130">只能通過在設定檔中註冊自訂模組來覆蓋預設模組。</span><span class="sxs-lookup"><span data-stu-id="21669-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="21669-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="21669-131">Configuration Files</span></span>  
 <span data-ttu-id="21669-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="21669-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21669-133">範例</span><span class="sxs-lookup"><span data-stu-id="21669-133">Example</span></span>  
 <span data-ttu-id="21669-134">以下示例註冊預設 HTTP 模組。</span><span class="sxs-lookup"><span data-stu-id="21669-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="21669-135">應將版本和 PublicKeyToken 的值替換為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="21669-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21669-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21669-136">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="21669-137">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="21669-137">Network Settings Schema</span></span>](index.md)
