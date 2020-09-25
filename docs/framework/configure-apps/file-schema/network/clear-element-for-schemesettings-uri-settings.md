---
title: schemeSettings 的 <clear> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 17069a56a8647871e98d70826a97a8fe407a0887
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205057"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="bf0df-102">schemeSettings 的 \<clear> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="bf0df-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="bf0df-103">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="bf0df-103">Clears all existing scheme settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="bf0df-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf0df-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf0df-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bf0df-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bf0df-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bf0df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf0df-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bf0df-107">Attributes</span></span>  

 <span data-ttu-id="bf0df-108">無。</span><span class="sxs-lookup"><span data-stu-id="bf0df-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf0df-109">子元素</span><span class="sxs-lookup"><span data-stu-id="bf0df-109">Child Elements</span></span>  

 <span data-ttu-id="bf0df-110">無。</span><span class="sxs-lookup"><span data-stu-id="bf0df-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf0df-111">父項目</span><span class="sxs-lookup"><span data-stu-id="bf0df-111">Parent Elements</span></span>  
  
|<span data-ttu-id="bf0df-112">項目</span><span class="sxs-lookup"><span data-stu-id="bf0df-112">Element</span></span>|<span data-ttu-id="bf0df-113">描述</span><span class="sxs-lookup"><span data-stu-id="bf0df-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf0df-114">\<schemeSettings> (Uri 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="bf0df-114">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="bf0df-115">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="bf0df-115">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf0df-116">備註</span><span class="sxs-lookup"><span data-stu-id="bf0df-116">Remarks</span></span>  

 <span data-ttu-id="bf0df-117">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bf0df-117">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="bf0df-118">這是為了抵禦如下攻擊的安全性機制：</span><span class="sxs-lookup"><span data-stu-id="bf0df-118">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="bf0df-119">如果將此 URI 傳遞給模組，但未正確處理已編碼的百分比字元，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bf0df-119">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="bf0df-120">基於這個理由， <xref:System.Uri?displayProperty=nameWithType> 類別會先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="bf0df-120">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="bf0df-121">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="bf0df-121">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="bf0df-122">您可以使用特定配置的 schemeSettings 設定選項，將此預設行為修改為不解除換用百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bf0df-122">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bf0df-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="bf0df-123">Configuration Files</span></span>  

 <span data-ttu-id="bf0df-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="bf0df-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0df-125">範例</span><span class="sxs-lookup"><span data-stu-id="bf0df-125">Example</span></span>  

 <span data-ttu-id="bf0df-126">下列範例顯示類別所使用的 <xref:System.Uri> 設定，此設定會清除所有配置設定，然後針對 HTTP 配置新增不會將百分比編碼路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="bf0df-126">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf0df-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf0df-127">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="bf0df-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bf0df-128">Network Settings Schema</span></span>](index.md)
