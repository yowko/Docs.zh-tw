---
title: "&lt;新增&gt;schemeSettings （Uri 設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ce4cc33d054e74fc9868a16764e744daf260c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="1db9b-102">&lt;新增&gt;schemeSettings （Uri 設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="1db9b-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="1db9b-103">新增配置名稱配置的設定。</span><span class="sxs-lookup"><span data-stu-id="1db9b-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="1db9b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1db9b-104">\<configuration></span></span>  
<span data-ttu-id="1db9b-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="1db9b-105">\<uri></span></span>  
<span data-ttu-id="1db9b-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="1db9b-106">\<schemeSettings></span></span>  
<span data-ttu-id="1db9b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="1db9b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db9b-108">語法</span><span class="sxs-lookup"><span data-stu-id="1db9b-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1db9b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1db9b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1db9b-110">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1db9b-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1db9b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1db9b-111">Attributes</span></span>  
  
|<span data-ttu-id="1db9b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1db9b-112">Attribute</span></span>|<span data-ttu-id="1db9b-113">描述</span><span class="sxs-lookup"><span data-stu-id="1db9b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1db9b-114">name</span><span class="sxs-lookup"><span data-stu-id="1db9b-114">name</span></span>|<span data-ttu-id="1db9b-115">此設定會套用的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="1db9b-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="1db9b-116">僅支援的值為 name ="http"及名稱 ="https"。</span><span class="sxs-lookup"><span data-stu-id="1db9b-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="1db9b-117">{屬性名稱}屬性</span><span class="sxs-lookup"><span data-stu-id="1db9b-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="1db9b-118">值</span><span class="sxs-lookup"><span data-stu-id="1db9b-118">Value</span></span>|<span data-ttu-id="1db9b-119">描述</span><span class="sxs-lookup"><span data-stu-id="1db9b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1db9b-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="1db9b-120">genericUriParserOptions</span></span>|<span data-ttu-id="1db9b-121">此配置剖析器選項。</span><span class="sxs-lookup"><span data-stu-id="1db9b-121">The parser options for this scheme.</span></span> <span data-ttu-id="1db9b-122">只支援值 genericUriParserOptions ="DontUnescapePathDotsAndSlashes"。</span><span class="sxs-lookup"><span data-stu-id="1db9b-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1db9b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="1db9b-123">Child Elements</span></span>  
 <span data-ttu-id="1db9b-124">無</span><span class="sxs-lookup"><span data-stu-id="1db9b-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1db9b-125">父項目</span><span class="sxs-lookup"><span data-stu-id="1db9b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1db9b-126">項目</span><span class="sxs-lookup"><span data-stu-id="1db9b-126">Element</span></span>|<span data-ttu-id="1db9b-127">說明</span><span class="sxs-lookup"><span data-stu-id="1db9b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1db9b-128">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="1db9b-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="1db9b-129">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="1db9b-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db9b-130">備註</span><span class="sxs-lookup"><span data-stu-id="1db9b-130">Remarks</span></span>  
 <span data-ttu-id="1db9b-131">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1db9b-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="1db9b-132">實作此點，做為安全性機制，攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1db9b-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1db9b-133">如果這個 URI 傳遞到模組未處理的百分之編碼字元正確，它可能會導致伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1db9b-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="1db9b-134">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1db9b-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="1db9b-135">傳遞至上方惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式會導致下列 URI:</span><span class="sxs-lookup"><span data-stu-id="1db9b-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1db9b-136">此預設行為修改為不取消逸出百分比編碼的路徑分隔符號使用的特定結構描述的 schemeSettings 組態選項。</span><span class="sxs-lookup"><span data-stu-id="1db9b-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1db9b-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="1db9b-137">Configuration Files</span></span>  
 <span data-ttu-id="1db9b-138">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1db9b-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db9b-139">範例</span><span class="sxs-lookup"><span data-stu-id="1db9b-139">Example</span></span>  
 <span data-ttu-id="1db9b-140">下列範例示範使用組態<xref:System.Uri>類別，以支援不逸出的 http 配置的百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1db9b-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1db9b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1db9b-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="1db9b-142">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1db9b-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
