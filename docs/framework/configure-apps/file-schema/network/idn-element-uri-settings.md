---
title: <idn> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698165"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="db82e-102">@no__t 0idn > 元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="db82e-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="db82e-103">指定是否要將國際化功能變數名稱（IDN）剖析套用至功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="db82e-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[<span data-ttu-id="db82e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="db82e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="db82e-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="db82e-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="db82e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<idn >**</span><span class="sxs-lookup"><span data-stu-id="db82e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db82e-107">語法</span><span class="sxs-lookup"><span data-stu-id="db82e-107">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db82e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="db82e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db82e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="db82e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db82e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="db82e-110">Attributes</span></span>  

|<span data-ttu-id="db82e-111">**目**</span><span class="sxs-lookup"><span data-stu-id="db82e-111">**Element**</span></span>|<span data-ttu-id="db82e-112">**描述**</span><span class="sxs-lookup"><span data-stu-id="db82e-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="db82e-113">指定是否將國際化功能變數名稱（IDN）剖析套用至功能變數名稱，預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="db82e-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="db82e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="db82e-114">Child elements</span></span>

<span data-ttu-id="db82e-115">None</span><span class="sxs-lookup"><span data-stu-id="db82e-115">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="db82e-116">父元素</span><span class="sxs-lookup"><span data-stu-id="db82e-116">Parent elements</span></span>

|<span data-ttu-id="db82e-117">**目**</span><span class="sxs-lookup"><span data-stu-id="db82e-117">**Element**</span></span>|<span data-ttu-id="db82e-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="db82e-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="db82e-119">uri</span><span class="sxs-lookup"><span data-stu-id="db82e-119">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="db82e-120">包含指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示之 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="db82e-120">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="db82e-121">備註</span><span class="sxs-lookup"><span data-stu-id="db82e-121">Remarks</span></span>

<span data-ttu-id="db82e-122">現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5 中擴充。</span><span class="sxs-lookup"><span data-stu-id="db82e-122">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="db82e-123">3.0 SP1 和 2.0 SP1，支援國際資源識別碼（IRI）和國際化功能變數名稱（IDN）。</span><span class="sxs-lookup"><span data-stu-id="db82e-123">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="db82e-124">目前的使用者除非特別啟用 IRI 和 IDN 支援，否則不會看到 .NET Framework 2.0 行為的任何變更。</span><span class="sxs-lookup"><span data-stu-id="db82e-124">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="db82e-125">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="db82e-125">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="db82e-126">若要啟用對 IRI 的支援，必須進行下列兩項變更：</span><span class="sxs-lookup"><span data-stu-id="db82e-126">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="db82e-127">將下面這一行新增至 machine.config 檔案的 .NET Framework 2.0 目錄底下：</span><span class="sxs-lookup"><span data-stu-id="db82e-127">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="db82e-128">指定是否要套用至功能變數名稱的國際化功能變數名稱（IDN）剖析，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="db82e-128">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="db82e-129">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="db82e-129">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="db82e-130">根據所使用的 DNS 伺服器，IDN 有三個可能的值：</span><span class="sxs-lookup"><span data-stu-id="db82e-130">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="db82e-131">已啟用 idn = 全部</span><span class="sxs-lookup"><span data-stu-id="db82e-131">idn enabled = All</span></span>  

     <span data-ttu-id="db82e-132">這個值會將任何 Unicode 功能變數名稱轉換成其 Punycode 對應項（IDN 名稱）。</span><span class="sxs-lookup"><span data-stu-id="db82e-132">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="db82e-133">已啟用 idn = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="db82e-133">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="db82e-134">這個值會將不在近端內部網路上的所有 Unicode 功能變數名稱轉換成使用 Punycode 對等專案（IDN 名稱）。</span><span class="sxs-lookup"><span data-stu-id="db82e-134">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="db82e-135">在此情況下，若要處理近端內部網路上的國際名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。</span><span class="sxs-lookup"><span data-stu-id="db82e-135">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="db82e-136">已啟用 idn = 無</span><span class="sxs-lookup"><span data-stu-id="db82e-136">idn enabled = None</span></span>

     <span data-ttu-id="db82e-137">這個值不會將任何 Unicode 功能變數名稱轉換成使用 Punycode。</span><span class="sxs-lookup"><span data-stu-id="db82e-137">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="db82e-138">這是與 .NET Framework 2.0 行為一致的預設值。</span><span class="sxs-lookup"><span data-stu-id="db82e-138">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="db82e-139">啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。</span><span class="sxs-lookup"><span data-stu-id="db82e-139">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="db82e-140">Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。</span><span class="sxs-lookup"><span data-stu-id="db82e-140">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="db82e-141">這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。</span><span class="sxs-lookup"><span data-stu-id="db82e-141">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="db82e-142">組態檔</span><span class="sxs-lookup"><span data-stu-id="db82e-142">Configuration files</span></span>

<span data-ttu-id="db82e-143">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="db82e-143">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="db82e-144">範例</span><span class="sxs-lookup"><span data-stu-id="db82e-144">Example</span></span>

<span data-ttu-id="db82e-145">下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定：</span><span class="sxs-lookup"><span data-stu-id="db82e-145">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="db82e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db82e-146">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="db82e-147">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="db82e-147">Network Settings Schema</span></span>](index.md)
