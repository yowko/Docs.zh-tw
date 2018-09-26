---
title: '&lt;清除&gt;schemeSettings （Uri 設定） 的項目'
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f0daa689ba09fa39ffe0f38d769112f0f095592a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47230835"
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="8a661-102">&lt;清除&gt;schemeSettings （Uri 設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="8a661-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="8a661-103">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="8a661-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="8a661-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8a661-104">\<configuration></span></span>  
<span data-ttu-id="8a661-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="8a661-105">\<uri></span></span>  
<span data-ttu-id="8a661-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="8a661-106">\<schemeSettings></span></span>  
<span data-ttu-id="8a661-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="8a661-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a661-108">語法</span><span class="sxs-lookup"><span data-stu-id="8a661-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a661-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8a661-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8a661-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8a661-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a661-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8a661-111">Attributes</span></span>  
 <span data-ttu-id="8a661-112">無。</span><span class="sxs-lookup"><span data-stu-id="8a661-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8a661-113">子元素</span><span class="sxs-lookup"><span data-stu-id="8a661-113">Child Elements</span></span>  
 <span data-ttu-id="8a661-114">無。</span><span class="sxs-lookup"><span data-stu-id="8a661-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a661-115">父項目</span><span class="sxs-lookup"><span data-stu-id="8a661-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8a661-116">項目</span><span class="sxs-lookup"><span data-stu-id="8a661-116">Element</span></span>|<span data-ttu-id="8a661-117">描述</span><span class="sxs-lookup"><span data-stu-id="8a661-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a661-118">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="8a661-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="8a661-119">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="8a661-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a661-120">備註</span><span class="sxs-lookup"><span data-stu-id="8a661-120">Remarks</span></span>  
 <span data-ttu-id="8a661-121">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，然後再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="8a661-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="8a661-122">這被實作為安全性機制，抵禦攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8a661-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8a661-123">如果這個 URI 會傳遞到模組不會處理百分比編碼字元正確，可能會造成伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8a661-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="8a661-124">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="8a661-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="8a661-125">傳遞至以上惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式結果，在下列 URI:</span><span class="sxs-lookup"><span data-stu-id="8a661-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="8a661-126">此預設行為可以修改為不取消逸出百分比編碼的路徑分隔符號使用 schemeSettings 組態選項的特定結構描述中。</span><span class="sxs-lookup"><span data-stu-id="8a661-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8a661-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="8a661-127">Configuration Files</span></span>  
 <span data-ttu-id="8a661-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="8a661-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a661-129">範例</span><span class="sxs-lookup"><span data-stu-id="8a661-129">Example</span></span>  
 <span data-ttu-id="8a661-130">下列範例顯示所使用的組態<xref:System.Uri>清除所有配置設定，然後將 支援的未逸出的 http 配置的百分比編碼的路徑分隔符號的類別。</span><span class="sxs-lookup"><span data-stu-id="8a661-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a661-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a661-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="8a661-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8a661-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
