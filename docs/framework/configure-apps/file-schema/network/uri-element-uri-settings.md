---
title: <uri> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697444"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="c1411-102">\<uri> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="c1411-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="c1411-103">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="c1411-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<uri>**  
  
## <a name="syntax"></a><span data-ttu-id="c1411-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1411-104">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1411-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1411-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c1411-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1411-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1411-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c1411-107">Attributes</span></span>  
 <span data-ttu-id="c1411-108">無。</span><span class="sxs-lookup"><span data-stu-id="c1411-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1411-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c1411-109">Child Elements</span></span>  
  
|<span data-ttu-id="c1411-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="c1411-110">**Element**</span></span>|<span data-ttu-id="c1411-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="c1411-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1411-112">idn</span><span class="sxs-lookup"><span data-stu-id="c1411-112">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="c1411-113">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="c1411-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="c1411-114">g</span><span class="sxs-lookup"><span data-stu-id="c1411-114">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="c1411-115">指定是否要套用國際資源識別碼（IRI）剖析 <xref:System.Uri> ，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="c1411-115">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="c1411-116">Schemesettings 專案</span><span class="sxs-lookup"><span data-stu-id="c1411-116">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="c1411-117">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="c1411-117">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1411-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c1411-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c1411-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="c1411-119">**Element**</span></span>|<span data-ttu-id="c1411-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="c1411-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c1411-121">設定</span><span class="sxs-lookup"><span data-stu-id="c1411-121">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="c1411-122">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="c1411-122">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1411-123">備註</span><span class="sxs-lookup"><span data-stu-id="c1411-123">Remarks</span></span>  
 <span data-ttu-id="c1411-124">`uri`元素包含 <xref:System.Uri> 命名空間中類別所使用之類別成員的設定 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="c1411-124">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="c1411-125">設定會設定 IRI 和 IDN 的支援。</span><span class="sxs-lookup"><span data-stu-id="c1411-125">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1411-126">範例</span><span class="sxs-lookup"><span data-stu-id="c1411-126">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c1411-127">描述</span><span class="sxs-lookup"><span data-stu-id="c1411-127">Description</span></span>  
 <span data-ttu-id="c1411-128">下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定。</span><span class="sxs-lookup"><span data-stu-id="c1411-128">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="c1411-129">此範例也會清除所有配置設定，然後針對 HTTP 配置新增不以轉義百分比編碼之路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="c1411-129">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c1411-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="c1411-130">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1411-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1411-131">See also</span></span>

- [<span data-ttu-id="c1411-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c1411-132">Network Settings Schema</span></span>](index.md)
