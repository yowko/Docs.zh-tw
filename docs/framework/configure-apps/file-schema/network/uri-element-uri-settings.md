---
title: <Uri> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663970"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="1e3f6-102">\<Uri > 元素 (Uri 設定)</span><span class="sxs-lookup"><span data-stu-id="1e3f6-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="1e3f6-103">包含指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="1e3f6-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="1e3f6-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="1e3f6-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="1e3f6-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="1e3f6-106">\<uri></span><span class="sxs-lookup"><span data-stu-id="1e3f6-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="1e3f6-107">語法</span><span class="sxs-lookup"><span data-stu-id="1e3f6-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e3f6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e3f6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e3f6-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e3f6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1e3f6-110">Attributes</span></span>  
 <span data-ttu-id="1e3f6-111">無。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e3f6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="1e3f6-112">Child Elements</span></span>  
  
|<span data-ttu-id="1e3f6-113">**目**</span><span class="sxs-lookup"><span data-stu-id="1e3f6-113">**Element**</span></span>|<span data-ttu-id="1e3f6-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="1e3f6-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1e3f6-115">idn</span><span class="sxs-lookup"><span data-stu-id="1e3f6-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="1e3f6-116">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="1e3f6-117">g</span><span class="sxs-lookup"><span data-stu-id="1e3f6-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="1e3f6-118">指定是否要<xref:System.Uri>套用國際資源識別碼 (IRI) 剖析, 以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="1e3f6-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="1e3f6-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="1e3f6-120">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e3f6-121">父項目</span><span class="sxs-lookup"><span data-stu-id="1e3f6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1e3f6-122">**目**</span><span class="sxs-lookup"><span data-stu-id="1e3f6-122">**Element**</span></span>|<span data-ttu-id="1e3f6-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="1e3f6-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1e3f6-124">configuration</span><span class="sxs-lookup"><span data-stu-id="1e3f6-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="1e3f6-125">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e3f6-126">備註</span><span class="sxs-lookup"><span data-stu-id="1e3f6-126">Remarks</span></span>  
 <span data-ttu-id="1e3f6-127">元素包含<xref:System.Net>命名空間中類別所<xref:System.Uri>使用之類別成員的設定。 `uri`</span><span class="sxs-lookup"><span data-stu-id="1e3f6-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="1e3f6-128">設定會設定 IRI 和 IDN 的支援。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e3f6-129">範例</span><span class="sxs-lookup"><span data-stu-id="1e3f6-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1e3f6-130">說明</span><span class="sxs-lookup"><span data-stu-id="1e3f6-130">Description</span></span>  
 <span data-ttu-id="1e3f6-131">下列範例顯示<xref:System.Uri>類別用來支援 IRI 剖析和 IDN 名稱的設定。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="1e3f6-132">此範例也會清除所有配置設定, 然後針對 HTTP 配置新增不以轉義百分比編碼之路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="1e3f6-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1e3f6-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="1e3f6-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e3f6-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e3f6-134">See also</span></span>

- [<span data-ttu-id="1e3f6-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1e3f6-135">Network Settings Schema</span></span>](index.md)
