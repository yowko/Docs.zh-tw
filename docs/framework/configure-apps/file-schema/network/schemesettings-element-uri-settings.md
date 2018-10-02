---
title: '&lt;schemeSettings&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 76ca5acc22eca07d372a2964cf3a6df4ea3b58d5
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48025304"
---
# <a name="ltschemesettingsgt-element-uri-settings"></a><span data-ttu-id="8e67c-102">&lt;schemeSettings&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="8e67c-102">&lt;schemeSettings&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="8e67c-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="8e67c-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="8e67c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8e67c-104">\<configuration></span></span>  
<span data-ttu-id="8e67c-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="8e67c-105">\<uri></span></span>  
<span data-ttu-id="8e67c-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="8e67c-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e67c-107">語法</span><span class="sxs-lookup"><span data-stu-id="8e67c-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e67c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e67c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8e67c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8e67c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e67c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8e67c-110">Attributes</span></span>  
 <span data-ttu-id="8e67c-111">無</span><span class="sxs-lookup"><span data-stu-id="8e67c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e67c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8e67c-112">Child Elements</span></span>  
  
|<span data-ttu-id="8e67c-113">**目**</span><span class="sxs-lookup"><span data-stu-id="8e67c-113">**Element**</span></span>|<span data-ttu-id="8e67c-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="8e67c-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8e67c-115">add</span><span class="sxs-lookup"><span data-stu-id="8e67c-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="8e67c-116">新增為結構描述名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="8e67c-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="8e67c-117">clear</span><span class="sxs-lookup"><span data-stu-id="8e67c-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="8e67c-118">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="8e67c-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="8e67c-119">remove</span><span class="sxs-lookup"><span data-stu-id="8e67c-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="8e67c-120">移除結構描述設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="8e67c-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e67c-121">父項目</span><span class="sxs-lookup"><span data-stu-id="8e67c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8e67c-122">**目**</span><span class="sxs-lookup"><span data-stu-id="8e67c-122">**Element**</span></span>|<span data-ttu-id="8e67c-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="8e67c-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8e67c-124">Uri</span><span class="sxs-lookup"><span data-stu-id="8e67c-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="8e67c-125">包含指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="8e67c-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e67c-126">備註</span><span class="sxs-lookup"><span data-stu-id="8e67c-126">Remarks</span></span>  
 <span data-ttu-id="8e67c-127">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，然後再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="8e67c-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8e67c-128">這被實作為安全性機制，抵禦攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8e67c-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8e67c-129">如果這個 URI 會傳遞到模組不會處理百分比編碼字元正確，可能會造成伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8e67c-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8e67c-130">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="8e67c-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8e67c-131">傳遞至以上惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式結果，在下列 URI:</span><span class="sxs-lookup"><span data-stu-id="8e67c-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8e67c-132">此預設行為可以修改為不取消逸出百分比編碼的路徑分隔符號使用 schemeSettings 組態選項的特定結構描述中。</span><span class="sxs-lookup"><span data-stu-id="8e67c-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8e67c-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="8e67c-133">Configuration Files</span></span>  
 <span data-ttu-id="8e67c-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="8e67c-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e67c-135">範例</span><span class="sxs-lookup"><span data-stu-id="8e67c-135">Example</span></span>  
 <span data-ttu-id="8e67c-136">下列範例顯示所使用的組態<xref:System.Uri>類別，以支援不逸出的 http 配置的百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8e67c-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="8e67c-137">項目資訊</span><span class="sxs-lookup"><span data-stu-id="8e67c-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="8e67c-138">命名空間</span><span class="sxs-lookup"><span data-stu-id="8e67c-138">Namespace</span></span>|<span data-ttu-id="8e67c-139">系統</span><span class="sxs-lookup"><span data-stu-id="8e67c-139">System</span></span>|  
|<span data-ttu-id="8e67c-140">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="8e67c-140">Schema Name</span></span>||  
|<span data-ttu-id="8e67c-141">驗證檔</span><span class="sxs-lookup"><span data-stu-id="8e67c-141">Validation File</span></span>||  
|<span data-ttu-id="8e67c-142">可以是空白</span><span class="sxs-lookup"><span data-stu-id="8e67c-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="8e67c-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e67c-143">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="8e67c-144">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8e67c-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
