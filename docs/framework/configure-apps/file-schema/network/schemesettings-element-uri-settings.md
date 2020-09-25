---
title: <schemeSettings> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 5a146b854239fd516125e66e05312e27b90c73ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91187013"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="9deee-102">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="9deee-102">\<schemeSettings> Element (Uri Settings)</span></span>

<span data-ttu-id="9deee-103">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="9deee-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="9deee-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9deee-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9deee-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9deee-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9deee-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9deee-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9deee-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9deee-107">Attributes</span></span>  

 <span data-ttu-id="9deee-108">無</span><span class="sxs-lookup"><span data-stu-id="9deee-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9deee-109">子元素</span><span class="sxs-lookup"><span data-stu-id="9deee-109">Child Elements</span></span>  
  
|<span data-ttu-id="9deee-110">**Element**</span><span class="sxs-lookup"><span data-stu-id="9deee-110">**Element**</span></span>|<span data-ttu-id="9deee-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="9deee-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9deee-112">add</span><span class="sxs-lookup"><span data-stu-id="9deee-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9deee-113">新增配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="9deee-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="9deee-114">清除</span><span class="sxs-lookup"><span data-stu-id="9deee-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9deee-115">清除所有現有的配置設定。</span><span class="sxs-lookup"><span data-stu-id="9deee-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="9deee-116">remove</span><span class="sxs-lookup"><span data-stu-id="9deee-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="9deee-117">移除配置名稱的配置設定。</span><span class="sxs-lookup"><span data-stu-id="9deee-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9deee-118">父項目</span><span class="sxs-lookup"><span data-stu-id="9deee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9deee-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="9deee-119">**Element**</span></span>|<span data-ttu-id="9deee-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="9deee-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9deee-121">uri</span><span class="sxs-lookup"><span data-stu-id="9deee-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="9deee-122">包含的設定會指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示的 web 位址。</span><span class="sxs-lookup"><span data-stu-id="9deee-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9deee-123">備註</span><span class="sxs-lookup"><span data-stu-id="9deee-123">Remarks</span></span>  

 <span data-ttu-id="9deee-124">根據預設， <xref:System.Uri?displayProperty=nameWithType> 類別會在執行路徑壓縮之前取消轉義百分比編碼的路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9deee-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="9deee-125">這是為了抵禦如下攻擊的安全性機制：</span><span class="sxs-lookup"><span data-stu-id="9deee-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9deee-126">如果將此 URI 傳遞給模組，但未正確處理已編碼的百分比字元，可能會導致伺服器執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9deee-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="9deee-127">基於這個理由， <xref:System.Uri?displayProperty=nameWithType> 類別會先取消轉義路徑分隔符號，然後套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="9deee-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="9deee-128">將上述惡意 URL 傳遞給類別的函式的結果會 <xref:System.Uri?displayProperty=nameWithType> 產生下列 URI：</span><span class="sxs-lookup"><span data-stu-id="9deee-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="9deee-129">您可以使用特定配置的 schemeSettings 設定選項，將此預設行為修改為不解除換用百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9deee-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9deee-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="9deee-130">Configuration Files</span></span>  

 <span data-ttu-id="9deee-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="9deee-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9deee-132">範例</span><span class="sxs-lookup"><span data-stu-id="9deee-132">Example</span></span>  

 <span data-ttu-id="9deee-133">下列範例顯示類別所使用的設定 <xref:System.Uri> ，以支援不將 HTTP 配置的百分比編碼路徑分隔符號進行轉義。</span><span class="sxs-lookup"><span data-stu-id="9deee-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="9deee-134">項目資訊</span><span class="sxs-lookup"><span data-stu-id="9deee-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="9deee-135">命名空間</span><span class="sxs-lookup"><span data-stu-id="9deee-135">Namespace</span></span>|<span data-ttu-id="9deee-136">系統</span><span class="sxs-lookup"><span data-stu-id="9deee-136">System</span></span>|  
|<span data-ttu-id="9deee-137">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="9deee-137">Schema Name</span></span>||  
|<span data-ttu-id="9deee-138">驗證檔</span><span class="sxs-lookup"><span data-stu-id="9deee-138">Validation File</span></span>||  
|<span data-ttu-id="9deee-139">可以是空的</span><span class="sxs-lookup"><span data-stu-id="9deee-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="9deee-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9deee-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="9deee-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9deee-141">Network Settings Schema</span></span>](index.md)
