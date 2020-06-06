---
title: schemeSettings 的 <remove> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089154"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="03b7a-102">schemeSettings 的 \<remove> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="03b7a-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="03b7a-103">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="03b7a-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="03b7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="03b7a-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b7a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03b7a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="03b7a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="03b7a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b7a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="03b7a-107">Attributes</span></span>  
  
|<span data-ttu-id="03b7a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="03b7a-108">Attribute</span></span>|<span data-ttu-id="03b7a-109">描述</span><span class="sxs-lookup"><span data-stu-id="03b7a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03b7a-110">NAME</span><span class="sxs-lookup"><span data-stu-id="03b7a-110">name</span></span>|<span data-ttu-id="03b7a-111">套用此設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="03b7a-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="03b7a-112">唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="03b7a-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03b7a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="03b7a-113">Child Elements</span></span>  
 <span data-ttu-id="03b7a-114">無。</span><span class="sxs-lookup"><span data-stu-id="03b7a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03b7a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="03b7a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="03b7a-116">元素</span><span class="sxs-lookup"><span data-stu-id="03b7a-116">Element</span></span>|<span data-ttu-id="03b7a-117">描述</span><span class="sxs-lookup"><span data-stu-id="03b7a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b7a-118">\<schemeSettings>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="03b7a-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="03b7a-119">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="03b7a-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b7a-120">備註</span><span class="sxs-lookup"><span data-stu-id="03b7a-120">Remarks</span></span>  
 <span data-ttu-id="03b7a-121">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="03b7a-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="03b7a-122">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="03b7a-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="03b7a-123">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="03b7a-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="03b7a-124">因此，類別會 <xref:System.Uri?displayProperty=nameWithType> 先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="03b7a-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="03b7a-125">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="03b7a-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="03b7a-126">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="03b7a-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03b7a-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="03b7a-127">Configuration Files</span></span>  
 <span data-ttu-id="03b7a-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="03b7a-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b7a-129">範例</span><span class="sxs-lookup"><span data-stu-id="03b7a-129">Example</span></span>  
 <span data-ttu-id="03b7a-130">下列範例 <xref:System.Uri> 會示範類別所使用的設定，其會移除 HTTP 配置的任何配置設定。</span><span class="sxs-lookup"><span data-stu-id="03b7a-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03b7a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03b7a-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="03b7a-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="03b7a-132">Network Settings Schema</span></span>](index.md)
