---
title: schemeSettings 的 <clear> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087448"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="3cf67-102">schemeSettings 的 \<clear> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="3cf67-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="3cf67-103">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="3cf67-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="3cf67-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cf67-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cf67-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3cf67-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3cf67-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3cf67-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cf67-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3cf67-107">Attributes</span></span>  
 <span data-ttu-id="3cf67-108">無。</span><span class="sxs-lookup"><span data-stu-id="3cf67-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3cf67-109">子元素</span><span class="sxs-lookup"><span data-stu-id="3cf67-109">Child Elements</span></span>  
 <span data-ttu-id="3cf67-110">無。</span><span class="sxs-lookup"><span data-stu-id="3cf67-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cf67-111">父項目</span><span class="sxs-lookup"><span data-stu-id="3cf67-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3cf67-112">元素</span><span class="sxs-lookup"><span data-stu-id="3cf67-112">Element</span></span>|<span data-ttu-id="3cf67-113">描述</span><span class="sxs-lookup"><span data-stu-id="3cf67-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cf67-114">\<schemeSettings>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="3cf67-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="3cf67-115">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="3cf67-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cf67-116">備註</span><span class="sxs-lookup"><span data-stu-id="3cf67-116">Remarks</span></span>  
 <span data-ttu-id="3cf67-117">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3cf67-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="3cf67-118">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="3cf67-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3cf67-119">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cf67-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="3cf67-120">因此，類別會 <xref:System.Uri?displayProperty=nameWithType> 先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="3cf67-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="3cf67-121">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="3cf67-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3cf67-122">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3cf67-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3cf67-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="3cf67-123">Configuration Files</span></span>  
 <span data-ttu-id="3cf67-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="3cf67-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cf67-125">範例</span><span class="sxs-lookup"><span data-stu-id="3cf67-125">Example</span></span>  
 <span data-ttu-id="3cf67-126">下列範例顯示的設定， <xref:System.Uri> 會清除所有配置設定，然後針對 HTTP 配置新增不以轉義百分比編碼的路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="3cf67-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3cf67-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cf67-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="3cf67-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3cf67-128">Network Settings Schema</span></span>](index.md)
