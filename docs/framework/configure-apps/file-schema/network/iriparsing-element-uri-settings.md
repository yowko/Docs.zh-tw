---
title: "&lt;iriParsing&gt;項目 （Uri 設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: aad2ea9a9255a6fc11465bae92f693065db21cb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="ffa45-102">&lt;iriParsing&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="ffa45-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="ffa45-103">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="ffa45-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="ffa45-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="ffa45-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="ffa45-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="ffa45-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ffa45-106">\<Uri > 項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="ffa45-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="ffa45-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="ffa45-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="ffa45-108">語法</span><span class="sxs-lookup"><span data-stu-id="ffa45-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffa45-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ffa45-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ffa45-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ffa45-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffa45-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ffa45-111">Attributes</span></span>  
  
|<span data-ttu-id="ffa45-112">**目**</span><span class="sxs-lookup"><span data-stu-id="ffa45-112">**Element**</span></span>|<span data-ttu-id="ffa45-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="ffa45-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ffa45-114">指定是否啟用 IRI 剖析。</span><span class="sxs-lookup"><span data-stu-id="ffa45-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="ffa45-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="ffa45-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffa45-116">子項目</span><span class="sxs-lookup"><span data-stu-id="ffa45-116">Child Elements</span></span>  
 <span data-ttu-id="ffa45-117">無</span><span class="sxs-lookup"><span data-stu-id="ffa45-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffa45-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ffa45-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ffa45-119">**目**</span><span class="sxs-lookup"><span data-stu-id="ffa45-119">**Element**</span></span>|<span data-ttu-id="ffa45-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="ffa45-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ffa45-121">uri</span><span class="sxs-lookup"><span data-stu-id="ffa45-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="ffa45-122">包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。</span><span class="sxs-lookup"><span data-stu-id="ffa45-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffa45-123">備註</span><span class="sxs-lookup"><span data-stu-id="ffa45-123">Remarks</span></span>  
 <span data-ttu-id="ffa45-124">現有<xref:System.Uri>類別已經過擴充，在.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="ffa45-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ffa45-125">3.0 SP1 和 2.0 SP1，以提供支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。</span><span class="sxs-lookup"><span data-stu-id="ffa45-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ffa45-126">目前的使用者不會看到從.NET Framework 2.0 行為的任何變更，除非它們特別啟用 IRI 和 IDN 支援。</span><span class="sxs-lookup"><span data-stu-id="ffa45-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ffa45-127">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="ffa45-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ffa45-128">若要啟用 IRI 的支援，下列兩項變更是必要的：</span><span class="sxs-lookup"><span data-stu-id="ffa45-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="ffa45-129">加入至 machine.config 檔案的.NET Framework 2.0 目錄下面這行</span><span class="sxs-lookup"><span data-stu-id="ffa45-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="ffa45-130">指定是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="ffa45-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ffa45-131">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="ffa45-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="ffa45-132">啟用 IRI 剖析 (啟用 iriParsing = `true`) 將會執行正規化和 RFC 3987 字元檢查最新 IRI 根據規則。</span><span class="sxs-lookup"><span data-stu-id="ffa45-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="ffa45-133">預設值是`false`會執行正規化和字元檢查根據 RFC 2396 和 RFC 3986 （適用於 IPv6 常值）。</span><span class="sxs-lookup"><span data-stu-id="ffa45-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="ffa45-134">組態檔</span><span class="sxs-lookup"><span data-stu-id="ffa45-134">Configuration Files</span></span>  
 <span data-ttu-id="ffa45-135">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ffa45-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffa45-136">範例</span><span class="sxs-lookup"><span data-stu-id="ffa45-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ffa45-137">說明</span><span class="sxs-lookup"><span data-stu-id="ffa45-137">Description</span></span>  
 <span data-ttu-id="ffa45-138">下列範例示範使用組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。</span><span class="sxs-lookup"><span data-stu-id="ffa45-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ffa45-139">程式碼</span><span class="sxs-lookup"><span data-stu-id="ffa45-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffa45-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffa45-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="ffa45-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ffa45-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
