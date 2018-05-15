---
title: '&lt;Uri&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 05b2fb4255643f657f37012ec51a1b29ed68095d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="2ac09-102">&lt;Uri&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="2ac09-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="2ac09-103">包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。</span><span class="sxs-lookup"><span data-stu-id="2ac09-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="2ac09-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="2ac09-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="2ac09-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="2ac09-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="2ac09-106">\<uri ></span><span class="sxs-lookup"><span data-stu-id="2ac09-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="2ac09-107">語法</span><span class="sxs-lookup"><span data-stu-id="2ac09-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ac09-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2ac09-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2ac09-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2ac09-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ac09-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2ac09-110">Attributes</span></span>  
 <span data-ttu-id="2ac09-111">無。</span><span class="sxs-lookup"><span data-stu-id="2ac09-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ac09-112">子項目</span><span class="sxs-lookup"><span data-stu-id="2ac09-112">Child Elements</span></span>  
  
|<span data-ttu-id="2ac09-113">**目**</span><span class="sxs-lookup"><span data-stu-id="2ac09-113">**Element**</span></span>|<span data-ttu-id="2ac09-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="2ac09-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2ac09-115">idn</span><span class="sxs-lookup"><span data-stu-id="2ac09-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="2ac09-116">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="2ac09-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="2ac09-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="2ac09-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="2ac09-118">指定是否套用國際資源識別項 (IRI) 剖析至<xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="2ac09-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="2ac09-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="2ac09-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="2ac09-120">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="2ac09-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ac09-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2ac09-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2ac09-122">**目**</span><span class="sxs-lookup"><span data-stu-id="2ac09-122">**Element**</span></span>|<span data-ttu-id="2ac09-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="2ac09-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2ac09-124">組態</span><span class="sxs-lookup"><span data-stu-id="2ac09-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2ac09-125">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="2ac09-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ac09-126">備註</span><span class="sxs-lookup"><span data-stu-id="2ac09-126">Remarks</span></span>  
 <span data-ttu-id="2ac09-127">`uri`項目包含的成員設定<xref:System.Uri>類別中的類別使用<xref:System.Net>命名空間。</span><span class="sxs-lookup"><span data-stu-id="2ac09-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="2ac09-128">這些設定會設定 IRI 和 IDN 支援。</span><span class="sxs-lookup"><span data-stu-id="2ac09-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ac09-129">範例</span><span class="sxs-lookup"><span data-stu-id="2ac09-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2ac09-130">描述</span><span class="sxs-lookup"><span data-stu-id="2ac09-130">Description</span></span>  
 <span data-ttu-id="2ac09-131">下列範例示範使用組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。</span><span class="sxs-lookup"><span data-stu-id="2ac09-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="2ac09-132">此範例也會清除所有配置設定，然後新增 支援的未逸出的 http 配置的百分比編碼路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2ac09-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2ac09-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="2ac09-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ac09-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac09-134">See Also</span></span>  
 [<span data-ttu-id="2ac09-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2ac09-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
