---
title: schemeSettings 的 <remove> 項目 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: fd137c86d7373947f57364c13eb3875cba46b269
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262621"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="1cf60-102">\<移除 > schemeSettings （Uri 設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="1cf60-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="1cf60-103">移除結構描述設定的配置名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf60-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="1cf60-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1cf60-104">\<configuration></span></span>  
<span data-ttu-id="1cf60-105">\<uri></span><span class="sxs-lookup"><span data-stu-id="1cf60-105">\<uri></span></span>  
<span data-ttu-id="1cf60-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="1cf60-106">\<schemeSettings></span></span>  
<span data-ttu-id="1cf60-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="1cf60-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf60-108">語法</span><span class="sxs-lookup"><span data-stu-id="1cf60-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cf60-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1cf60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1cf60-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1cf60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cf60-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1cf60-111">Attributes</span></span>  
  
|<span data-ttu-id="1cf60-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1cf60-112">Attribute</span></span>|<span data-ttu-id="1cf60-113">描述</span><span class="sxs-lookup"><span data-stu-id="1cf60-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cf60-114">名稱</span><span class="sxs-lookup"><span data-stu-id="1cf60-114">name</span></span>|<span data-ttu-id="1cf60-115">這項設定適用於配置名稱。</span><span class="sxs-lookup"><span data-stu-id="1cf60-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="1cf60-116">僅支援的值為名稱 ="http"和名稱 ="https"。</span><span class="sxs-lookup"><span data-stu-id="1cf60-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cf60-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1cf60-117">Child Elements</span></span>  
 <span data-ttu-id="1cf60-118">無。</span><span class="sxs-lookup"><span data-stu-id="1cf60-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cf60-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1cf60-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1cf60-120">項目</span><span class="sxs-lookup"><span data-stu-id="1cf60-120">Element</span></span>|<span data-ttu-id="1cf60-121">描述</span><span class="sxs-lookup"><span data-stu-id="1cf60-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cf60-122">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="1cf60-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="1cf60-123">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="1cf60-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cf60-124">備註</span><span class="sxs-lookup"><span data-stu-id="1cf60-124">Remarks</span></span>  
 <span data-ttu-id="1cf60-125">根據預設，<xref:System.Uri?displayProperty=nameWithType>類別取消逸出百分比編碼路徑分隔符號，然後再執行路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1cf60-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="1cf60-126">這被實作為安全性機制，抵禦攻擊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1cf60-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1cf60-127">如果這個 URI 會傳遞到模組不會處理百分比編碼字元正確，可能會造成伺服器正在執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="1cf60-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="1cf60-128">基於這個理由，<xref:System.Uri?displayProperty=nameWithType>類別第一個取消逸出路徑分隔符號，然後再套用路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1cf60-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="1cf60-129">傳遞至以上惡意 URL 的結果<xref:System.Uri?displayProperty=nameWithType>類別建構函式結果，在下列 URI:</span><span class="sxs-lookup"><span data-stu-id="1cf60-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="1cf60-130">此預設行為可以修改為不取消逸出百分比編碼的路徑分隔符號使用 schemeSettings 組態選項的特定結構描述中。</span><span class="sxs-lookup"><span data-stu-id="1cf60-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1cf60-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="1cf60-131">Configuration Files</span></span>  
 <span data-ttu-id="1cf60-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1cf60-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cf60-133">範例</span><span class="sxs-lookup"><span data-stu-id="1cf60-133">Example</span></span>  
 <span data-ttu-id="1cf60-134">下列範例顯示所使用的組態<xref:System.Uri>移除 http 配置的任何配置設定的類別。</span><span class="sxs-lookup"><span data-stu-id="1cf60-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cf60-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cf60-135">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="1cf60-136">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1cf60-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
