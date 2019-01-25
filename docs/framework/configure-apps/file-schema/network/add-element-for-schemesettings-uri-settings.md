---
title: '&lt;新增&gt;schemeSettings （Uri 設定） 的項目'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: d64744cf3c88d5ec0f0edf1a31cdf184c3c8277e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524100"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="cf050-102">&lt;新增&gt;schemeSettings （Uri 設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="cf050-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="cf050-103">新增為結構描述名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="cf050-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="cf050-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cf050-104">\<configuration></span></span>  
<span data-ttu-id="cf050-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="cf050-105">\<uri></span></span>  
<span data-ttu-id="cf050-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="cf050-106">\<schemeSettings></span></span>  
<span data-ttu-id="cf050-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cf050-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf050-108">語法</span><span class="sxs-lookup"><span data-stu-id="cf050-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf050-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf050-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cf050-110">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="cf050-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf050-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cf050-111">Attributes</span></span>  
  
|<span data-ttu-id="cf050-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cf050-112">Attribute</span></span>|<span data-ttu-id="cf050-113">描述</span><span class="sxs-lookup"><span data-stu-id="cf050-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf050-114">名稱</span><span class="sxs-lookup"><span data-stu-id="cf050-114">name</span></span>|<span data-ttu-id="cf050-115">這項設定適用於配置名稱。</span><span class="sxs-lookup"><span data-stu-id="cf050-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="cf050-116">僅支援的值為名稱 ="http"和名稱 ="https"。</span><span class="sxs-lookup"><span data-stu-id="cf050-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="cf050-117">{屬性 name}屬性</span><span class="sxs-lookup"><span data-stu-id="cf050-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="cf050-118">值</span><span class="sxs-lookup"><span data-stu-id="cf050-118">Value</span></span>|<span data-ttu-id="cf050-119">描述</span><span class="sxs-lookup"><span data-stu-id="cf050-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cf050-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="cf050-120">genericUriParserOptions</span></span>|<span data-ttu-id="cf050-121">此配置剖析器選項。</span><span class="sxs-lookup"><span data-stu-id="cf050-121">The parser options for this scheme.</span></span> <span data-ttu-id="cf050-122">僅支援的值是 genericUriParserOptions ="DontUnescapePathDotsAndSlashes 」。</span><span class="sxs-lookup"><span data-stu-id="cf050-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf050-123">子元素</span><span class="sxs-lookup"><span data-stu-id="cf050-123">Child Elements</span></span>  
 <span data-ttu-id="cf050-124">無</span><span class="sxs-lookup"><span data-stu-id="cf050-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf050-125">父項目</span><span class="sxs-lookup"><span data-stu-id="cf050-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cf050-126">項目</span><span class="sxs-lookup"><span data-stu-id="cf050-126">Element</span></span>|<span data-ttu-id="cf050-127">描述</span><span class="sxs-lookup"><span data-stu-id="cf050-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf050-128">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="cf050-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="cf050-129">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="cf050-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf050-130">備註</span><span class="sxs-lookup"><span data-stu-id="cf050-130">Remarks</span></span>  
 <span data-ttu-id="cf050-131">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，然後再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="cf050-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="cf050-132">這被實作為安全性機制，抵禦攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cf050-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="cf050-133">如果這個 URI 會傳遞到模組不會處理百分比編碼字元正確，可能會造成伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="cf050-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="cf050-134">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="cf050-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="cf050-135">傳遞至以上惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式結果，在下列 URI:</span><span class="sxs-lookup"><span data-stu-id="cf050-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="cf050-136">此預設行為可以修改為不取消逸出百分比編碼的路徑分隔符號使用 schemeSettings 組態選項的特定結構描述中。</span><span class="sxs-lookup"><span data-stu-id="cf050-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cf050-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="cf050-137">Configuration Files</span></span>  
 <span data-ttu-id="cf050-138">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="cf050-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf050-139">範例</span><span class="sxs-lookup"><span data-stu-id="cf050-139">Example</span></span>  
 <span data-ttu-id="cf050-140">下列範例顯示所使用的組態<xref:System.Uri>類別，以支援不逸出的 http 配置的百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="cf050-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf050-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf050-141">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="cf050-142">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cf050-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
