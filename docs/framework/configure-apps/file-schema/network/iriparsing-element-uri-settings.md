---
title: <iriParsing> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 7033f4dcda7d2fe73310ae0d36d9b05c090d13d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299666"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="83144-102">\<Iriparsing> > 項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="83144-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="83144-103">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="83144-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="83144-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="83144-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="83144-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="83144-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="83144-106">\<Uri > 項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="83144-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="83144-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="83144-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="83144-108">語法</span><span class="sxs-lookup"><span data-stu-id="83144-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83144-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83144-109">Attributes and Elements</span></span>  
 <span data-ttu-id="83144-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="83144-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83144-111">屬性</span><span class="sxs-lookup"><span data-stu-id="83144-111">Attributes</span></span>  
  
|<span data-ttu-id="83144-112">**目**</span><span class="sxs-lookup"><span data-stu-id="83144-112">**Element**</span></span>|<span data-ttu-id="83144-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="83144-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="83144-114">指定是否啟用 IRI 剖析。</span><span class="sxs-lookup"><span data-stu-id="83144-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="83144-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="83144-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83144-116">子元素</span><span class="sxs-lookup"><span data-stu-id="83144-116">Child Elements</span></span>  
 <span data-ttu-id="83144-117">None</span><span class="sxs-lookup"><span data-stu-id="83144-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83144-118">父項目</span><span class="sxs-lookup"><span data-stu-id="83144-118">Parent Elements</span></span>  
  
|<span data-ttu-id="83144-119">**目**</span><span class="sxs-lookup"><span data-stu-id="83144-119">**Element**</span></span>|<span data-ttu-id="83144-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="83144-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83144-121">uri</span><span class="sxs-lookup"><span data-stu-id="83144-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="83144-122">包含指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="83144-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83144-123">備註</span><span class="sxs-lookup"><span data-stu-id="83144-123">Remarks</span></span>  
 <span data-ttu-id="83144-124">現有<xref:System.Uri>類別已擴充.NET Framework 3.5 中。</span><span class="sxs-lookup"><span data-stu-id="83144-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="83144-125">3.0 SP1 和 2.0 SP1 提供支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。</span><span class="sxs-lookup"><span data-stu-id="83144-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="83144-126">目前的使用者不會看到任何變更從.NET Framework 2.0 的行為，除非它們特別啟用 IRI 和 IDN 支援。</span><span class="sxs-lookup"><span data-stu-id="83144-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="83144-127">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="83144-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="83144-128">若要啟用 IRI 支援，下列兩項變更是必要的：</span><span class="sxs-lookup"><span data-stu-id="83144-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="83144-129">將下行新增至.NET Framework 2.0 目錄下的 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="83144-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="83144-130">指定是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="83144-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="83144-131">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="83144-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="83144-132">啟用 IRI 剖析 (啟用 Iriparsing> = `true`) 會執行正規化和字元檢查根據最新的 IRI 規則在 RFC 3987。</span><span class="sxs-lookup"><span data-stu-id="83144-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="83144-133">預設值是`false`會執行正規化和字元檢查根據 RFC 2396 和 RFC 3986 （適用於 IPv6 常值）。</span><span class="sxs-lookup"><span data-stu-id="83144-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="83144-134">組態檔</span><span class="sxs-lookup"><span data-stu-id="83144-134">Configuration Files</span></span>  
 <span data-ttu-id="83144-135">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="83144-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83144-136">範例</span><span class="sxs-lookup"><span data-stu-id="83144-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="83144-137">描述</span><span class="sxs-lookup"><span data-stu-id="83144-137">Description</span></span>  
 <span data-ttu-id="83144-138">下列範例顯示所使用的組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。</span><span class="sxs-lookup"><span data-stu-id="83144-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="83144-139">程式碼</span><span class="sxs-lookup"><span data-stu-id="83144-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83144-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83144-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="83144-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="83144-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
