---
title: schemeSettings 的 <clear> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 51c669aff767948523172aa075677ad3fb6478a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664170"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="0d9e8-102">\<清除 Schemesettings 專案的 > 元素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="0d9e8-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="0d9e8-103">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="0d9e8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0d9e8-104">\<configuration></span></span>  
<span data-ttu-id="0d9e8-105">\<uri ></span><span class="sxs-lookup"><span data-stu-id="0d9e8-105">\<uri></span></span>  
<span data-ttu-id="0d9e8-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="0d9e8-106">\<schemeSettings></span></span>  
<span data-ttu-id="0d9e8-107">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="0d9e8-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9e8-108">語法</span><span class="sxs-lookup"><span data-stu-id="0d9e8-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d9e8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d9e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0d9e8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d9e8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0d9e8-111">Attributes</span></span>  
 <span data-ttu-id="0d9e8-112">無。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d9e8-113">子元素</span><span class="sxs-lookup"><span data-stu-id="0d9e8-113">Child Elements</span></span>  
 <span data-ttu-id="0d9e8-114">無。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d9e8-115">父項目</span><span class="sxs-lookup"><span data-stu-id="0d9e8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0d9e8-116">項目</span><span class="sxs-lookup"><span data-stu-id="0d9e8-116">Element</span></span>|<span data-ttu-id="0d9e8-117">描述</span><span class="sxs-lookup"><span data-stu-id="0d9e8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d9e8-118">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="0d9e8-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="0d9e8-119">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d9e8-120">備註</span><span class="sxs-lookup"><span data-stu-id="0d9e8-120">Remarks</span></span>  
 <span data-ttu-id="0d9e8-121">根據預設, <xref:System.Uri?displayProperty=nameWithType>類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0d9e8-122">這會實作為安全性機制來對抗下列攻擊:</span><span class="sxs-lookup"><span data-stu-id="0d9e8-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0d9e8-123">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組, 可能會導致伺服器執行下列命令:</span><span class="sxs-lookup"><span data-stu-id="0d9e8-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0d9e8-124">因此, <xref:System.Uri?displayProperty=nameWithType>類別會先取消轉義路徑分隔符號, 然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0d9e8-125">將上述惡意 URL 傳遞給<xref:System.Uri?displayProperty=nameWithType>類別的函式的結果會產生下列 URI:</span><span class="sxs-lookup"><span data-stu-id="0d9e8-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0d9e8-126">您可以使用特定配置的 Schemesettings 專案設定選項, 修改這個預設行為, 而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0d9e8-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="0d9e8-127">Configuration Files</span></span>  
 <span data-ttu-id="0d9e8-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d9e8-129">範例</span><span class="sxs-lookup"><span data-stu-id="0d9e8-129">Example</span></span>  
 <span data-ttu-id="0d9e8-130">下列範例顯示的<xref:System.Uri>設定, 會清除所有配置設定, 然後針對 HTTP 配置新增不以轉義百分比編碼的路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="0d9e8-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d9e8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9e8-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="0d9e8-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0d9e8-132">Network Settings Schema</span></span>](index.md)
