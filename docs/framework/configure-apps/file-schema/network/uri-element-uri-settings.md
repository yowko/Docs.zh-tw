---
title: <uri> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697444"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="05b82-102">@no__t 0uri > 元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="05b82-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="05b82-103">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="05b82-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="05b82-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="05b82-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="05b82-105">&nbsp; @ no__t-1 **\<uri >**</span><span class="sxs-lookup"><span data-stu-id="05b82-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b82-106">語法</span><span class="sxs-lookup"><span data-stu-id="05b82-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05b82-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05b82-107">Attributes and Elements</span></span>  
 <span data-ttu-id="05b82-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="05b82-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05b82-109">屬性</span><span class="sxs-lookup"><span data-stu-id="05b82-109">Attributes</span></span>  
 <span data-ttu-id="05b82-110">無。</span><span class="sxs-lookup"><span data-stu-id="05b82-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05b82-111">子元素</span><span class="sxs-lookup"><span data-stu-id="05b82-111">Child Elements</span></span>  
  
|<span data-ttu-id="05b82-112">**目**</span><span class="sxs-lookup"><span data-stu-id="05b82-112">**Element**</span></span>|<span data-ttu-id="05b82-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="05b82-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05b82-114">idn</span><span class="sxs-lookup"><span data-stu-id="05b82-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="05b82-115">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="05b82-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="05b82-116">g</span><span class="sxs-lookup"><span data-stu-id="05b82-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="05b82-117">指定是否要將國際資源識別碼（IRI）剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="05b82-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="05b82-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="05b82-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="05b82-119">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="05b82-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05b82-120">父項目</span><span class="sxs-lookup"><span data-stu-id="05b82-120">Parent Elements</span></span>  
  
|<span data-ttu-id="05b82-121">**目**</span><span class="sxs-lookup"><span data-stu-id="05b82-121">**Element**</span></span>|<span data-ttu-id="05b82-122">**描述**</span><span class="sxs-lookup"><span data-stu-id="05b82-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05b82-123">configuration</span><span class="sxs-lookup"><span data-stu-id="05b82-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="05b82-124">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="05b82-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05b82-125">備註</span><span class="sxs-lookup"><span data-stu-id="05b82-125">Remarks</span></span>  
 <span data-ttu-id="05b82-126">@No__t-0 元素包含 <xref:System.Net> 命名空間中的類別所使用之 @no__t 1 類別成員的設定。</span><span class="sxs-lookup"><span data-stu-id="05b82-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="05b82-127">設定會設定 IRI 和 IDN 的支援。</span><span class="sxs-lookup"><span data-stu-id="05b82-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05b82-128">範例</span><span class="sxs-lookup"><span data-stu-id="05b82-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="05b82-129">描述</span><span class="sxs-lookup"><span data-stu-id="05b82-129">Description</span></span>  
 <span data-ttu-id="05b82-130">下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定。</span><span class="sxs-lookup"><span data-stu-id="05b82-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="05b82-131">此範例也會清除所有配置設定，然後針對 HTTP 配置新增不以轉義百分比編碼之路徑分隔符號的支援。</span><span class="sxs-lookup"><span data-stu-id="05b82-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="05b82-132">程式碼</span><span class="sxs-lookup"><span data-stu-id="05b82-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05b82-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05b82-133">See also</span></span>

- [<span data-ttu-id="05b82-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="05b82-134">Network Settings Schema</span></span>](index.md)
