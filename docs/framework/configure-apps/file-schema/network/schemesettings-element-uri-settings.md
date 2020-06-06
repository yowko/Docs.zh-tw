---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154643"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="225ba-102">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="225ba-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="225ba-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="225ba-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="225ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="225ba-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="225ba-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="225ba-105">Attributes and Elements</span></span>  
 <span data-ttu-id="225ba-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="225ba-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="225ba-107">屬性</span><span class="sxs-lookup"><span data-stu-id="225ba-107">Attributes</span></span>  
 <span data-ttu-id="225ba-108">無</span><span class="sxs-lookup"><span data-stu-id="225ba-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="225ba-109">子元素</span><span class="sxs-lookup"><span data-stu-id="225ba-109">Child Elements</span></span>  
  
|<span data-ttu-id="225ba-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="225ba-110">**Element**</span></span>|<span data-ttu-id="225ba-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="225ba-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="225ba-112">add</span><span class="sxs-lookup"><span data-stu-id="225ba-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="225ba-113">新增配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="225ba-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="225ba-114">明確</span><span class="sxs-lookup"><span data-stu-id="225ba-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="225ba-115">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="225ba-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="225ba-116">remove</span><span class="sxs-lookup"><span data-stu-id="225ba-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="225ba-117">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="225ba-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="225ba-118">父項目</span><span class="sxs-lookup"><span data-stu-id="225ba-118">Parent Elements</span></span>  
  
|<span data-ttu-id="225ba-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="225ba-119">**Element**</span></span>|<span data-ttu-id="225ba-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="225ba-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="225ba-121">uri</span><span class="sxs-lookup"><span data-stu-id="225ba-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="225ba-122">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="225ba-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225ba-123">備註</span><span class="sxs-lookup"><span data-stu-id="225ba-123">Remarks</span></span>  
 <span data-ttu-id="225ba-124">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="225ba-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="225ba-125">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="225ba-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="225ba-126">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="225ba-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="225ba-127">因此，類別會 <xref:System.Uri?displayProperty=nameWithType> 先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="225ba-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="225ba-128">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="225ba-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="225ba-129">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="225ba-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="225ba-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="225ba-130">Configuration Files</span></span>  
 <span data-ttu-id="225ba-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="225ba-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="225ba-132">範例</span><span class="sxs-lookup"><span data-stu-id="225ba-132">Example</span></span>  
 <span data-ttu-id="225ba-133">下列範例顯示類別所使用的設定 <xref:System.Uri> ，以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。</span><span class="sxs-lookup"><span data-stu-id="225ba-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="225ba-134">項目資訊</span><span class="sxs-lookup"><span data-stu-id="225ba-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="225ba-135">命名空間</span><span class="sxs-lookup"><span data-stu-id="225ba-135">Namespace</span></span>|<span data-ttu-id="225ba-136">系統</span><span class="sxs-lookup"><span data-stu-id="225ba-136">System</span></span>|  
|<span data-ttu-id="225ba-137">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="225ba-137">Schema Name</span></span>||  
|<span data-ttu-id="225ba-138">驗證檔</span><span class="sxs-lookup"><span data-stu-id="225ba-138">Validation File</span></span>||  
|<span data-ttu-id="225ba-139">可以是空的</span><span class="sxs-lookup"><span data-stu-id="225ba-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="225ba-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="225ba-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="225ba-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="225ba-141">Network Settings Schema</span></span>](index.md)
