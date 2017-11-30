---
title: "&lt;webRequestModules&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac20d3da42b150734abbbd36c4ec9fc2e60b6216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a><span data-ttu-id="8f1c8-102">&lt;webRequestModules&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="8f1c8-102">&lt;webRequestModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8f1c8-103">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-103">Specifies modules to use to request information from network hosts.</span></span>  
  
 <span data-ttu-id="8f1c8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8f1c8-104">\<configuration></span></span>  
<span data-ttu-id="8f1c8-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="8f1c8-105">\<system.net></span></span>  
<span data-ttu-id="8f1c8-106">\<webRequestModules ></span><span class="sxs-lookup"><span data-stu-id="8f1c8-106">\<webRequestModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1c8-107">語法</span><span class="sxs-lookup"><span data-stu-id="8f1c8-107">Syntax</span></span>  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f1c8-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8f1c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8f1c8-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f1c8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8f1c8-110">Attributes</span></span>  
 <span data-ttu-id="8f1c8-111">無。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8f1c8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8f1c8-112">Child Elements</span></span>  
  
|<span data-ttu-id="8f1c8-113">**目**</span><span class="sxs-lookup"><span data-stu-id="8f1c8-113">**Element**</span></span>|<span data-ttu-id="8f1c8-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="8f1c8-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8f1c8-115">add</span><span class="sxs-lookup"><span data-stu-id="8f1c8-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="8f1c8-116">將自訂的 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-116">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="8f1c8-117">clear</span><span class="sxs-lookup"><span data-stu-id="8f1c8-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="8f1c8-118">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-118">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="8f1c8-119">remove</span><span class="sxs-lookup"><span data-stu-id="8f1c8-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="8f1c8-120">移除應用程式中自訂的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-120">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8f1c8-121">父項目</span><span class="sxs-lookup"><span data-stu-id="8f1c8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8f1c8-122">**目**</span><span class="sxs-lookup"><span data-stu-id="8f1c8-122">**Element**</span></span>|<span data-ttu-id="8f1c8-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="8f1c8-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8f1c8-124">system.net</span><span class="sxs-lookup"><span data-stu-id="8f1c8-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="8f1c8-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f1c8-126">備註</span><span class="sxs-lookup"><span data-stu-id="8f1c8-126">Remarks</span></span>  
 <span data-ttu-id="8f1c8-127">`webRequestModules` 項目會註冊 <xref:System.Net.WebRequest> 類別的子系，以處理對網路主機的資訊要求。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-127">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="8f1c8-128">Web 要求的模組必須實作<xref:System.Net.IWebRequestCreate>介面。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-128">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="8f1c8-129">.NET Framework 包含開頭為 http://、 https:// 和 file:// Uri Web 要求的模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-129">The .NET Framework includes Web request modules for URIs that begin with http://, https://, and file://.</span></span> <span data-ttu-id="8f1c8-130">您可以覆寫預設的模組只有在組態檔中註冊自訂的模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-130">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8f1c8-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="8f1c8-131">Configuration Files</span></span>  
 <span data-ttu-id="8f1c8-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f1c8-133">範例</span><span class="sxs-lookup"><span data-stu-id="8f1c8-133">Example</span></span>  
 <span data-ttu-id="8f1c8-134">下列範例會註冊預設的 HTTP 模組。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-134">The following example registers the default HTTP module.</span></span> <span data-ttu-id="8f1c8-135">您應該取得版本和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="8f1c8-135">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f1c8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f1c8-136">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [<span data-ttu-id="8f1c8-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8f1c8-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
