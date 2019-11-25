---
title: schemeSettings 的 <remove> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089154"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="3cd03-102">\<移除 Schemesettings 專案的 > 元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="3cd03-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="3cd03-103">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="3cd03-103">Removes a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="3cd03-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3cd03-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3cd03-105">&nbsp;&nbsp;[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3cd03-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="3cd03-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemesettings 專案 >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3cd03-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="3cd03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="3cd03-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3cd03-108">語法</span><span class="sxs-lookup"><span data-stu-id="3cd03-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cd03-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3cd03-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3cd03-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3cd03-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cd03-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3cd03-111">Attributes</span></span>  
  
|<span data-ttu-id="3cd03-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3cd03-112">Attribute</span></span>|<span data-ttu-id="3cd03-113">描述</span><span class="sxs-lookup"><span data-stu-id="3cd03-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3cd03-114">NAME</span><span class="sxs-lookup"><span data-stu-id="3cd03-114">name</span></span>|<span data-ttu-id="3cd03-115">套用此設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="3cd03-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="3cd03-116">唯一支援的值為 name = "HTTP" 和 name = "HTTPs"。</span><span class="sxs-lookup"><span data-stu-id="3cd03-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cd03-117">子項目</span><span class="sxs-lookup"><span data-stu-id="3cd03-117">Child Elements</span></span>  
 <span data-ttu-id="3cd03-118">無。</span><span class="sxs-lookup"><span data-stu-id="3cd03-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3cd03-119">父項目</span><span class="sxs-lookup"><span data-stu-id="3cd03-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3cd03-120">項目</span><span class="sxs-lookup"><span data-stu-id="3cd03-120">Element</span></span>|<span data-ttu-id="3cd03-121">描述</span><span class="sxs-lookup"><span data-stu-id="3cd03-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3cd03-122">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="3cd03-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="3cd03-123">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="3cd03-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cd03-124">備註</span><span class="sxs-lookup"><span data-stu-id="3cd03-124">Remarks</span></span>  
 <span data-ttu-id="3cd03-125">根據預設，<xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3cd03-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="3cd03-126">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="3cd03-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3cd03-127">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="3cd03-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="3cd03-128">基於這個理由，<xref:System.Uri?displayProperty=nameWithType> 類別會先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="3cd03-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="3cd03-129">將上述惡意 URL 傳遞給 <xref:System.Uri?displayProperty=nameWithType> 類別的函式，會產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="3cd03-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="3cd03-130">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3cd03-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3cd03-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="3cd03-131">Configuration Files</span></span>  
 <span data-ttu-id="3cd03-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="3cd03-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd03-133">範例</span><span class="sxs-lookup"><span data-stu-id="3cd03-133">Example</span></span>  
 <span data-ttu-id="3cd03-134">下列範例會顯示 <xref:System.Uri> 類別所使用的設定，以移除 HTTP 配置的任何配置設定。</span><span class="sxs-lookup"><span data-stu-id="3cd03-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cd03-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cd03-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="3cd03-136">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3cd03-136">Network Settings Schema</span></span>](index.md)
