---
title: '&lt;idn&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="550c4-102">&lt;idn&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="550c4-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="550c4-103">指定是否國際化網域名稱 (IDN) 剖析會套用至網域名稱。</span><span class="sxs-lookup"><span data-stu-id="550c4-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="550c4-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="550c4-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="550c4-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="550c4-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="550c4-106">\<Uri > 項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="550c4-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="550c4-107">\<idn ></span><span class="sxs-lookup"><span data-stu-id="550c4-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="550c4-108">語法</span><span class="sxs-lookup"><span data-stu-id="550c4-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="550c4-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="550c4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="550c4-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="550c4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="550c4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="550c4-111">Attributes</span></span>  
  
|<span data-ttu-id="550c4-112">**目**</span><span class="sxs-lookup"><span data-stu-id="550c4-112">**Element**</span></span>|<span data-ttu-id="550c4-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="550c4-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="550c4-114">指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱的預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="550c4-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="550c4-115">子項目</span><span class="sxs-lookup"><span data-stu-id="550c4-115">Child Elements</span></span>  
 <span data-ttu-id="550c4-116">無</span><span class="sxs-lookup"><span data-stu-id="550c4-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="550c4-117">父項目</span><span class="sxs-lookup"><span data-stu-id="550c4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="550c4-118">**目**</span><span class="sxs-lookup"><span data-stu-id="550c4-118">**Element**</span></span>|<span data-ttu-id="550c4-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="550c4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="550c4-120">Uri</span><span class="sxs-lookup"><span data-stu-id="550c4-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="550c4-121">包含會指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址設定。</span><span class="sxs-lookup"><span data-stu-id="550c4-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="550c4-122">備註</span><span class="sxs-lookup"><span data-stu-id="550c4-122">Remarks</span></span>  
 <span data-ttu-id="550c4-123">現有<xref:System.Uri>類別已經過擴充，在.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="550c4-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="550c4-124">3.0 SP1 和 2.0 SP1，可以支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。</span><span class="sxs-lookup"><span data-stu-id="550c4-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="550c4-125">目前的使用者不會看到從.NET Framework 2.0 行為的任何變更，除非它們特別啟用 IRI 和 IDN 支援。</span><span class="sxs-lookup"><span data-stu-id="550c4-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="550c4-126">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="550c4-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="550c4-127">若要啟用 IRI 的支援，下列兩項變更是必要的：</span><span class="sxs-lookup"><span data-stu-id="550c4-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="550c4-128">加入至 machine.config 檔案的.NET Framework 2.0 目錄下面這行</span><span class="sxs-lookup"><span data-stu-id="550c4-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="550c4-129">指定是否要國際化網域名稱 (IDN) 剖析套用至網域名稱，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="550c4-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="550c4-130">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="550c4-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="550c4-131">有三個可能的值為 IDN 根據所使用的 DNS 伺服器：</span><span class="sxs-lookup"><span data-stu-id="550c4-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="550c4-132">啟用 idn = All</span><span class="sxs-lookup"><span data-stu-id="550c4-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="550c4-133">這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等 （IDN 名稱）。</span><span class="sxs-lookup"><span data-stu-id="550c4-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="550c4-134">啟用 idn = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="550c4-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="550c4-135">此值將轉換為不在近端內部網路使用 Punycode 對等項目 （IDN 名稱） 上的所有 Unicode 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="550c4-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="550c4-136">在此情況下，若要處理國際性近端內部網路上的名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。</span><span class="sxs-lookup"><span data-stu-id="550c4-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="550c4-137">啟用 idn = 無</span><span class="sxs-lookup"><span data-stu-id="550c4-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="550c4-138">此值不會將轉換使用 Punycode 任何 Unicode 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="550c4-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="550c4-139">這是預設值是與.NET Framework 2.0 的行為一致。</span><span class="sxs-lookup"><span data-stu-id="550c4-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="550c4-140">啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。</span><span class="sxs-lookup"><span data-stu-id="550c4-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="550c4-141">Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。</span><span class="sxs-lookup"><span data-stu-id="550c4-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="550c4-142">這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。</span><span class="sxs-lookup"><span data-stu-id="550c4-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="550c4-143">組態檔</span><span class="sxs-lookup"><span data-stu-id="550c4-143">Configuration Files</span></span>  
 <span data-ttu-id="550c4-144">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="550c4-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="550c4-145">範例</span><span class="sxs-lookup"><span data-stu-id="550c4-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="550c4-146">描述</span><span class="sxs-lookup"><span data-stu-id="550c4-146">Description</span></span>  
 <span data-ttu-id="550c4-147">下列範例示範使用組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。</span><span class="sxs-lookup"><span data-stu-id="550c4-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="550c4-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="550c4-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="550c4-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="550c4-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="550c4-150">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="550c4-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
