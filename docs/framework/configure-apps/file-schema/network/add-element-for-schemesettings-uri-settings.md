---
title: schemeSettings 的 <add> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087722"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="b8e02-102">schemeSettings 的 \<add> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="b8e02-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="b8e02-103">新增配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="b8e02-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="b8e02-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8e02-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e02-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8e02-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e02-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b8e02-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e02-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e02-107">Attributes</span></span>  
  
|<span data-ttu-id="b8e02-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e02-108">Attribute</span></span>|<span data-ttu-id="b8e02-109">描述</span><span class="sxs-lookup"><span data-stu-id="b8e02-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8e02-110">NAME</span><span class="sxs-lookup"><span data-stu-id="b8e02-110">name</span></span>|<span data-ttu-id="b8e02-111">套用此設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="b8e02-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="b8e02-112">唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="b8e02-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="b8e02-113">{屬性名稱}特性</span><span class="sxs-lookup"><span data-stu-id="b8e02-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="b8e02-114">值</span><span class="sxs-lookup"><span data-stu-id="b8e02-114">Value</span></span>|<span data-ttu-id="b8e02-115">描述</span><span class="sxs-lookup"><span data-stu-id="b8e02-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8e02-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="b8e02-116">genericUriParserOptions</span></span>|<span data-ttu-id="b8e02-117">此配置的剖析器選項。</span><span class="sxs-lookup"><span data-stu-id="b8e02-117">The parser options for this scheme.</span></span> <span data-ttu-id="b8e02-118">唯一支援的值為 genericUriParserOptions = "DontUnescapePathDotsAndSlashes"。</span><span class="sxs-lookup"><span data-stu-id="b8e02-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8e02-119">子元素</span><span class="sxs-lookup"><span data-stu-id="b8e02-119">Child Elements</span></span>  
 <span data-ttu-id="b8e02-120">無</span><span class="sxs-lookup"><span data-stu-id="b8e02-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e02-121">父項目</span><span class="sxs-lookup"><span data-stu-id="b8e02-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e02-122">元素</span><span class="sxs-lookup"><span data-stu-id="b8e02-122">Element</span></span>|<span data-ttu-id="b8e02-123">描述</span><span class="sxs-lookup"><span data-stu-id="b8e02-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e02-124">\<schemeSettings>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="b8e02-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b8e02-125">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="b8e02-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e02-126">備註</span><span class="sxs-lookup"><span data-stu-id="b8e02-126">Remarks</span></span>  
 <span data-ttu-id="b8e02-127">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b8e02-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="b8e02-128">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="b8e02-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b8e02-129">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="b8e02-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="b8e02-130">因此，類別會 <xref:System.Uri?displayProperty=nameWithType> 先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="b8e02-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="b8e02-131">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8e02-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b8e02-132">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b8e02-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8e02-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="b8e02-133">Configuration Files</span></span>  
 <span data-ttu-id="b8e02-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="b8e02-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e02-135">範例</span><span class="sxs-lookup"><span data-stu-id="b8e02-135">Example</span></span>  
 <span data-ttu-id="b8e02-136">下列範例顯示類別所使用的設定 <xref:System.Uri> ，以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。</span><span class="sxs-lookup"><span data-stu-id="b8e02-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8e02-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e02-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="b8e02-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b8e02-138">Network Settings Schema</span></span>](index.md)
