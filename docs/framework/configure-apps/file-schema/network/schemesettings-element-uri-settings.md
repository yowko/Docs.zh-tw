---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154643"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="4f929-102">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="4f929-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="4f929-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="4f929-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="4f929-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="4f929-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4f929-105">&nbsp;&nbsp;[**\<烏裡>**](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4f929-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="4f929-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<方案設置>**</span><span class="sxs-lookup"><span data-stu-id="4f929-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f929-107">語法</span><span class="sxs-lookup"><span data-stu-id="4f929-107">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f929-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f929-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4f929-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f929-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f929-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4f929-110">Attributes</span></span>  
 <span data-ttu-id="4f929-111">None</span><span class="sxs-lookup"><span data-stu-id="4f929-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f929-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4f929-112">Child Elements</span></span>  
  
|<span data-ttu-id="4f929-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="4f929-113">**Element**</span></span>|<span data-ttu-id="4f929-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="4f929-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4f929-115">新增</span><span class="sxs-lookup"><span data-stu-id="4f929-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4f929-116">添加方案名稱的方案設置。</span><span class="sxs-lookup"><span data-stu-id="4f929-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="4f929-117">清楚</span><span class="sxs-lookup"><span data-stu-id="4f929-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4f929-118">清除所有現有方案設置。</span><span class="sxs-lookup"><span data-stu-id="4f929-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="4f929-119">移除</span><span class="sxs-lookup"><span data-stu-id="4f929-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4f929-120">刪除方案名稱的方案設置。</span><span class="sxs-lookup"><span data-stu-id="4f929-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f929-121">父項目</span><span class="sxs-lookup"><span data-stu-id="4f929-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f929-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="4f929-122">**Element**</span></span>|<span data-ttu-id="4f929-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="4f929-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4f929-124">Uri</span><span class="sxs-lookup"><span data-stu-id="4f929-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="4f929-125">包含指定 .NET 框架如何處理使用統一資源識別項 （URI） 表示的 Web 位址的設置。</span><span class="sxs-lookup"><span data-stu-id="4f929-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f929-126">備註</span><span class="sxs-lookup"><span data-stu-id="4f929-126">Remarks</span></span>  
 <span data-ttu-id="4f929-127">預設情況下，<xref:System.Uri?displayProperty=nameWithType>類取消轉義百分比編碼的路徑分隔符號，然後再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="4f929-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="4f929-128">這是作為針對以下攻擊的安全機制實現的：</span><span class="sxs-lookup"><span data-stu-id="4f929-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f929-129">如果此 URI 傳遞給未正確處理編碼百分比的模組，則可能導致伺服器執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4f929-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="4f929-130">因此，<xref:System.Uri?displayProperty=nameWithType>類首先取消轉義路徑分隔符號，然後應用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="4f929-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="4f929-131">將上述惡意 URL 傳遞給<xref:System.Uri?displayProperty=nameWithType>類建構函式的結果會導致以下 URI：</span><span class="sxs-lookup"><span data-stu-id="4f929-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4f929-132">可以使用方案設置配置選項修改此預設行為，以不取消轉義百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="4f929-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4f929-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="4f929-133">Configuration Files</span></span>  
 <span data-ttu-id="4f929-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="4f929-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f929-135">範例</span><span class="sxs-lookup"><span data-stu-id="4f929-135">Example</span></span>  
 <span data-ttu-id="4f929-136">下面的示例顯示了<xref:System.Uri>類用於支援不為 HTTP 方案提供百分比編碼的路徑分隔符號的配置。</span><span class="sxs-lookup"><span data-stu-id="4f929-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="4f929-137">項目資訊</span><span class="sxs-lookup"><span data-stu-id="4f929-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="4f929-138">命名空間</span><span class="sxs-lookup"><span data-stu-id="4f929-138">Namespace</span></span>|<span data-ttu-id="4f929-139">系統</span><span class="sxs-lookup"><span data-stu-id="4f929-139">System</span></span>|  
|<span data-ttu-id="4f929-140">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="4f929-140">Schema Name</span></span>||  
|<span data-ttu-id="4f929-141">驗證檔</span><span class="sxs-lookup"><span data-stu-id="4f929-141">Validation File</span></span>||  
|<span data-ttu-id="4f929-142">可以為空</span><span class="sxs-lookup"><span data-stu-id="4f929-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="4f929-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f929-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="4f929-144">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="4f929-144">Network Settings Schema</span></span>](index.md)
