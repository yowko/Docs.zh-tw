---
title: schemeSettings 的 <remove> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 018a08693a39bb297bdaa468ba59d4bf097f6922
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151385"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="9afe1-102">schemeSettings 的 \<remove> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="9afe1-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>

<span data-ttu-id="9afe1-103">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="9afe1-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="9afe1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9afe1-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9afe1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9afe1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9afe1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9afe1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9afe1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9afe1-107">Attributes</span></span>  
  
|<span data-ttu-id="9afe1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9afe1-108">Attribute</span></span>|<span data-ttu-id="9afe1-109">描述</span><span class="sxs-lookup"><span data-stu-id="9afe1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9afe1-110">NAME</span><span class="sxs-lookup"><span data-stu-id="9afe1-110">name</span></span>|<span data-ttu-id="9afe1-111">套用此設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="9afe1-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="9afe1-112">唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="9afe1-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9afe1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="9afe1-113">Child Elements</span></span>  

 <span data-ttu-id="9afe1-114">無。</span><span class="sxs-lookup"><span data-stu-id="9afe1-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9afe1-115">父項目</span><span class="sxs-lookup"><span data-stu-id="9afe1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9afe1-116">項目</span><span class="sxs-lookup"><span data-stu-id="9afe1-116">Element</span></span>|<span data-ttu-id="9afe1-117">描述</span><span class="sxs-lookup"><span data-stu-id="9afe1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9afe1-118">\<schemeSettings> (Uri 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="9afe1-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="9afe1-119">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="9afe1-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9afe1-120">備註</span><span class="sxs-lookup"><span data-stu-id="9afe1-120">Remarks</span></span>  

 <span data-ttu-id="9afe1-121">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9afe1-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="9afe1-122">這是為了抵禦如下攻擊的安全性機制：</span><span class="sxs-lookup"><span data-stu-id="9afe1-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9afe1-123">如果將此 URI 傳遞給模組，但未正確處理已編碼的百分比字元，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9afe1-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="9afe1-124">基於這個理由， <xref:System.Uri?displayProperty=nameWithType> 類別會先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="9afe1-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="9afe1-125">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="9afe1-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9afe1-126">您可以使用特定配置的 schemeSettings 設定選項，將此預設行為修改為不解除換用百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9afe1-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9afe1-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="9afe1-127">Configuration Files</span></span>  

 <span data-ttu-id="9afe1-128">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="9afe1-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9afe1-129">範例</span><span class="sxs-lookup"><span data-stu-id="9afe1-129">Example</span></span>  

 <span data-ttu-id="9afe1-130">下列範例顯示 <xref:System.Uri> 類別所使用的設定，此設定會移除 HTTP 配置的任何配置設定。</span><span class="sxs-lookup"><span data-stu-id="9afe1-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9afe1-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9afe1-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="9afe1-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9afe1-132">Network Settings Schema</span></span>](index.md)
