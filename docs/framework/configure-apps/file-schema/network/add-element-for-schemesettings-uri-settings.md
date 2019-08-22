---
title: schemeSettings 的 <add> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659546"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="1bd5e-102">\<新增 Schemesettings 專案的 > 元素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="1bd5e-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="1bd5e-103">新增配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="1bd5e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1bd5e-104">\<configuration></span></span>  
<span data-ttu-id="1bd5e-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="1bd5e-105">\<uri></span></span>  
<span data-ttu-id="1bd5e-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="1bd5e-106">\<schemeSettings></span></span>  
<span data-ttu-id="1bd5e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="1bd5e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd5e-108">語法</span><span class="sxs-lookup"><span data-stu-id="1bd5e-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bd5e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1bd5e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1bd5e-110">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1bd5e-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bd5e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1bd5e-111">Attributes</span></span>  
  
|<span data-ttu-id="1bd5e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1bd5e-112">Attribute</span></span>|<span data-ttu-id="1bd5e-113">描述</span><span class="sxs-lookup"><span data-stu-id="1bd5e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1bd5e-114">NAME</span><span class="sxs-lookup"><span data-stu-id="1bd5e-114">name</span></span>|<span data-ttu-id="1bd5e-115">套用此設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="1bd5e-116">唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="1bd5e-117">{屬性名稱}特性</span><span class="sxs-lookup"><span data-stu-id="1bd5e-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="1bd5e-118">值</span><span class="sxs-lookup"><span data-stu-id="1bd5e-118">Value</span></span>|<span data-ttu-id="1bd5e-119">說明</span><span class="sxs-lookup"><span data-stu-id="1bd5e-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1bd5e-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="1bd5e-120">genericUriParserOptions</span></span>|<span data-ttu-id="1bd5e-121">此配置的剖析器選項。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-121">The parser options for this scheme.</span></span> <span data-ttu-id="1bd5e-122">唯一支援的值為 genericUriParserOptions = "DontUnescapePathDotsAndSlashes"。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bd5e-123">子元素</span><span class="sxs-lookup"><span data-stu-id="1bd5e-123">Child Elements</span></span>  
 <span data-ttu-id="1bd5e-124">None</span><span class="sxs-lookup"><span data-stu-id="1bd5e-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bd5e-125">父項目</span><span class="sxs-lookup"><span data-stu-id="1bd5e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1bd5e-126">項目</span><span class="sxs-lookup"><span data-stu-id="1bd5e-126">Element</span></span>|<span data-ttu-id="1bd5e-127">描述</span><span class="sxs-lookup"><span data-stu-id="1bd5e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1bd5e-128">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="1bd5e-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="1bd5e-129">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd5e-130">備註</span><span class="sxs-lookup"><span data-stu-id="1bd5e-130">Remarks</span></span>  
 <span data-ttu-id="1bd5e-131">根據預設, <xref:System.Uri?displayProperty=nameWithType>類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="1bd5e-132">這會實作為安全性機制來對抗下列攻擊:</span><span class="sxs-lookup"><span data-stu-id="1bd5e-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1bd5e-133">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組, 可能會導致伺服器執行下列命令:</span><span class="sxs-lookup"><span data-stu-id="1bd5e-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="1bd5e-134">因此, <xref:System.Uri?displayProperty=nameWithType>類別會先取消轉義路徑分隔符號, 然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="1bd5e-135">將上述惡意 URL 傳遞給<xref:System.Uri?displayProperty=nameWithType>類別的函式的結果會產生下列 URI:</span><span class="sxs-lookup"><span data-stu-id="1bd5e-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1bd5e-136">您可以使用特定配置的 Schemesettings 專案設定選項, 修改這個預設行為, 而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1bd5e-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="1bd5e-137">Configuration Files</span></span>  
 <span data-ttu-id="1bd5e-138">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bd5e-139">範例</span><span class="sxs-lookup"><span data-stu-id="1bd5e-139">Example</span></span>  
 <span data-ttu-id="1bd5e-140">下列範例顯示類別所<xref:System.Uri>使用的設定, 以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bd5e-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bd5e-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="1bd5e-142">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1bd5e-142">Network Settings Schema</span></span>](index.md)
