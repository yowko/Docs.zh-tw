---
title: "&lt;schemeSettings&gt;項目 （Uri 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4cf1d2013a51985f9d7772ac0ef86e5dbb120be9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltschemesettingsgt-element-uri-settings"></a><span data-ttu-id="e50e5-102">&lt;schemeSettings&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="e50e5-102">&lt;schemeSettings&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="e50e5-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="e50e5-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="e50e5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e50e5-104">\<configuration></span></span>  
<span data-ttu-id="e50e5-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="e50e5-105">\<uri></span></span>  
<span data-ttu-id="e50e5-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="e50e5-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50e5-107">語法</span><span class="sxs-lookup"><span data-stu-id="e50e5-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e50e5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e50e5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e50e5-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e50e5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e50e5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e50e5-110">Attributes</span></span>  
 <span data-ttu-id="e50e5-111">無</span><span class="sxs-lookup"><span data-stu-id="e50e5-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e50e5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e50e5-112">Child Elements</span></span>  
  
|<span data-ttu-id="e50e5-113">**目**</span><span class="sxs-lookup"><span data-stu-id="e50e5-113">**Element**</span></span>|<span data-ttu-id="e50e5-114">**說明**</span><span class="sxs-lookup"><span data-stu-id="e50e5-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e50e5-115">add</span><span class="sxs-lookup"><span data-stu-id="e50e5-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e50e5-116">新增配置名稱配置的設定。</span><span class="sxs-lookup"><span data-stu-id="e50e5-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="e50e5-117">clear</span><span class="sxs-lookup"><span data-stu-id="e50e5-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e50e5-118">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="e50e5-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="e50e5-119">remove</span><span class="sxs-lookup"><span data-stu-id="e50e5-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="e50e5-120">移除配置設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="e50e5-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e50e5-121">父項目</span><span class="sxs-lookup"><span data-stu-id="e50e5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e50e5-122">**目**</span><span class="sxs-lookup"><span data-stu-id="e50e5-122">**Element**</span></span>|<span data-ttu-id="e50e5-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="e50e5-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e50e5-124">uri</span><span class="sxs-lookup"><span data-stu-id="e50e5-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="e50e5-125">包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。</span><span class="sxs-lookup"><span data-stu-id="e50e5-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e50e5-126">備註</span><span class="sxs-lookup"><span data-stu-id="e50e5-126">Remarks</span></span>  
 <span data-ttu-id="e50e5-127">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="e50e5-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="e50e5-128">實作此點，做為安全性機制，攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e50e5-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e50e5-129">如果這個 URI 傳遞到模組未處理的百分之編碼字元正確，它可能會導致伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e50e5-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="e50e5-130">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="e50e5-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="e50e5-131">傳遞至上方惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式會導致下列 URI:</span><span class="sxs-lookup"><span data-stu-id="e50e5-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="e50e5-132">此預設行為修改為不取消逸出百分比編碼的路徑分隔符號使用的特定結構描述的 schemeSettings 組態選項。</span><span class="sxs-lookup"><span data-stu-id="e50e5-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e50e5-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="e50e5-133">Configuration Files</span></span>  
 <span data-ttu-id="e50e5-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="e50e5-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e50e5-135">範例</span><span class="sxs-lookup"><span data-stu-id="e50e5-135">Example</span></span>  
 <span data-ttu-id="e50e5-136">下列範例示範使用組態<xref:System.Uri>類別，以支援不逸出的 http 配置的百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="e50e5-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="e50e5-137">項目資訊</span><span class="sxs-lookup"><span data-stu-id="e50e5-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="e50e5-138">命名空間</span><span class="sxs-lookup"><span data-stu-id="e50e5-138">Namespace</span></span>|<span data-ttu-id="e50e5-139">系統</span><span class="sxs-lookup"><span data-stu-id="e50e5-139">System</span></span>|  
|<span data-ttu-id="e50e5-140">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="e50e5-140">Schema Name</span></span>||  
|<span data-ttu-id="e50e5-141">驗證檔</span><span class="sxs-lookup"><span data-stu-id="e50e5-141">Validation File</span></span>||  
|<span data-ttu-id="e50e5-142">可以是空白</span><span class="sxs-lookup"><span data-stu-id="e50e5-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e50e5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e50e5-143">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="e50e5-144">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e50e5-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
