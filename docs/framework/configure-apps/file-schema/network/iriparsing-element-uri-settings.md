---
title: <iriParsing> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698097"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="62787-102">@no__t 0iriParsing > 元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="62787-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="62787-103">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="62787-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="62787-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="62787-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="62787-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="62787-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="62787-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<iriParsing >**</span><span class="sxs-lookup"><span data-stu-id="62787-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62787-107">語法</span><span class="sxs-lookup"><span data-stu-id="62787-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62787-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62787-108">Attributes and Elements</span></span>  
 <span data-ttu-id="62787-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="62787-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62787-110">屬性</span><span class="sxs-lookup"><span data-stu-id="62787-110">Attributes</span></span>  
  
|<span data-ttu-id="62787-111">**目**</span><span class="sxs-lookup"><span data-stu-id="62787-111">**Element**</span></span>|<span data-ttu-id="62787-112">**描述**</span><span class="sxs-lookup"><span data-stu-id="62787-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="62787-113">指定是否啟用 IRI 剖析。</span><span class="sxs-lookup"><span data-stu-id="62787-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="62787-114">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="62787-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62787-115">子元素</span><span class="sxs-lookup"><span data-stu-id="62787-115">Child Elements</span></span>  
 <span data-ttu-id="62787-116">None</span><span class="sxs-lookup"><span data-stu-id="62787-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62787-117">父項目</span><span class="sxs-lookup"><span data-stu-id="62787-117">Parent Elements</span></span>  
  
|<span data-ttu-id="62787-118">**目**</span><span class="sxs-lookup"><span data-stu-id="62787-118">**Element**</span></span>|<span data-ttu-id="62787-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="62787-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="62787-120">uri</span><span class="sxs-lookup"><span data-stu-id="62787-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="62787-121">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="62787-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62787-122">備註</span><span class="sxs-lookup"><span data-stu-id="62787-122">Remarks</span></span>  
 <span data-ttu-id="62787-123">現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5 中擴充。</span><span class="sxs-lookup"><span data-stu-id="62787-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="62787-124">3.0 SP1 和 2.0 SP1，以提供國際資源識別碼（IRI）和國際化功能變數名稱（IDN）的支援。</span><span class="sxs-lookup"><span data-stu-id="62787-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="62787-125">目前的使用者除非特別啟用 IRI 和 IDN 支援，否則不會看到 .NET Framework 2.0 行為的任何變更。</span><span class="sxs-lookup"><span data-stu-id="62787-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="62787-126">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="62787-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="62787-127">若要啟用對 IRI 的支援，必須進行下列兩項變更：</span><span class="sxs-lookup"><span data-stu-id="62787-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="62787-128">將下行新增至 machine.config 檔案的 .NET Framework 2.0 目錄底下</span><span class="sxs-lookup"><span data-stu-id="62787-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="62787-129">指定是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="62787-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="62787-130">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="62787-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="62787-131">啟用 IRI 剖析（g enabled = `true`）會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查。</span><span class="sxs-lookup"><span data-stu-id="62787-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="62787-132">預設值為 `false`，將會根據 RFC 2396 和 RFC 3986 （適用于 IPv6 常值）進行正規化和字元檢查。</span><span class="sxs-lookup"><span data-stu-id="62787-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="62787-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="62787-133">Configuration Files</span></span>  
 <span data-ttu-id="62787-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="62787-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62787-135">範例</span><span class="sxs-lookup"><span data-stu-id="62787-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="62787-136">描述</span><span class="sxs-lookup"><span data-stu-id="62787-136">Description</span></span>  
 <span data-ttu-id="62787-137">下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定。</span><span class="sxs-lookup"><span data-stu-id="62787-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="62787-138">程式碼</span><span class="sxs-lookup"><span data-stu-id="62787-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62787-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62787-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="62787-140">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="62787-140">Network Settings Schema</span></span>](index.md)
