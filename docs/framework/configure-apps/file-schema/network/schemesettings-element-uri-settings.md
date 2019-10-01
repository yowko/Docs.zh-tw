---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 498aef77a1dfd8cffcac73b704b8d1bb6df5d165
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697762"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="ecdcb-102">@no__t 0schemeSettings > 元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="ecdcb-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="ecdcb-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="ecdcb-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="ecdcb-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ecdcb-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ecdcb-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="ecdcb-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<schemeSettings >**</span><span class="sxs-lookup"><span data-stu-id="ecdcb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecdcb-107">語法</span><span class="sxs-lookup"><span data-stu-id="ecdcb-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecdcb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ecdcb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ecdcb-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecdcb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ecdcb-110">Attributes</span></span>  
 <span data-ttu-id="ecdcb-111">None</span><span class="sxs-lookup"><span data-stu-id="ecdcb-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecdcb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ecdcb-112">Child Elements</span></span>  
  
|<span data-ttu-id="ecdcb-113">**目**</span><span class="sxs-lookup"><span data-stu-id="ecdcb-113">**Element**</span></span>|<span data-ttu-id="ecdcb-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="ecdcb-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ecdcb-115">add</span><span class="sxs-lookup"><span data-stu-id="ecdcb-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="ecdcb-116">新增配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="ecdcb-117">clear</span><span class="sxs-lookup"><span data-stu-id="ecdcb-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="ecdcb-118">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="ecdcb-119">remove</span><span class="sxs-lookup"><span data-stu-id="ecdcb-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="ecdcb-120">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecdcb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="ecdcb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ecdcb-122">**目**</span><span class="sxs-lookup"><span data-stu-id="ecdcb-122">**Element**</span></span>|<span data-ttu-id="ecdcb-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="ecdcb-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ecdcb-124">uri</span><span class="sxs-lookup"><span data-stu-id="ecdcb-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="ecdcb-125">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecdcb-126">備註</span><span class="sxs-lookup"><span data-stu-id="ecdcb-126">Remarks</span></span>  
 <span data-ttu-id="ecdcb-127">根據預設，在執行路徑壓縮之前，@no__t 0 類別會取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ecdcb-128">這會實作為安全性機制來對抗下列攻擊：</span><span class="sxs-lookup"><span data-stu-id="ecdcb-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ecdcb-129">如果將此 URI 向下傳遞至未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ecdcb-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ecdcb-130">因此，<xref:System.Uri?displayProperty=nameWithType> 類別會先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ecdcb-131">將上述惡意 URL 傳遞給 @no__t 0 類別的函式，會產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="ecdcb-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ecdcb-132">您可以使用特定配置的 Schemesettings 專案設定選項，修改這個預設行為，而不要解除轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ecdcb-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="ecdcb-133">Configuration Files</span></span>  
 <span data-ttu-id="ecdcb-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecdcb-135">範例</span><span class="sxs-lookup"><span data-stu-id="ecdcb-135">Example</span></span>  
 <span data-ttu-id="ecdcb-136">下列範例顯示 <xref:System.Uri> 類別所使用的設定，以支援不要將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。</span><span class="sxs-lookup"><span data-stu-id="ecdcb-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="ecdcb-137">項目資訊</span><span class="sxs-lookup"><span data-stu-id="ecdcb-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="ecdcb-138">命名空間</span><span class="sxs-lookup"><span data-stu-id="ecdcb-138">Namespace</span></span>|<span data-ttu-id="ecdcb-139">系統</span><span class="sxs-lookup"><span data-stu-id="ecdcb-139">System</span></span>|  
|<span data-ttu-id="ecdcb-140">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="ecdcb-140">Schema Name</span></span>||  
|<span data-ttu-id="ecdcb-141">驗證檔</span><span class="sxs-lookup"><span data-stu-id="ecdcb-141">Validation File</span></span>||  
|<span data-ttu-id="ecdcb-142">可以是空的</span><span class="sxs-lookup"><span data-stu-id="ecdcb-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="ecdcb-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecdcb-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="ecdcb-144">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ecdcb-144">Network Settings Schema</span></span>](index.md)
