---
title: '&lt;idn&gt;項目 （Uri 設定）'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1537c17cb3c16beeb41cfaa4103e0664e93facc7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170596"
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="4f10b-102">&lt;idn&gt;項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="4f10b-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="4f10b-103">指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱。</span><span class="sxs-lookup"><span data-stu-id="4f10b-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="4f10b-104">結構描述階層架構</span><span class="sxs-lookup"><span data-stu-id="4f10b-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="4f10b-105">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="4f10b-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="4f10b-106">\<Uri > 項目 （Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="4f10b-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="4f10b-107">\<idn ></span><span class="sxs-lookup"><span data-stu-id="4f10b-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="4f10b-108">語法</span><span class="sxs-lookup"><span data-stu-id="4f10b-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f10b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f10b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4f10b-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4f10b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f10b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4f10b-111">Attributes</span></span>  
  
|<span data-ttu-id="4f10b-112">**目**</span><span class="sxs-lookup"><span data-stu-id="4f10b-112">**Element**</span></span>|<span data-ttu-id="4f10b-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="4f10b-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="4f10b-114">指定是否國際化網域名稱 (IDN) 剖析套用至網域名稱的預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="4f10b-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f10b-115">子項目</span><span class="sxs-lookup"><span data-stu-id="4f10b-115">Child Elements</span></span>  
 <span data-ttu-id="4f10b-116">無</span><span class="sxs-lookup"><span data-stu-id="4f10b-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f10b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4f10b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4f10b-118">**目**</span><span class="sxs-lookup"><span data-stu-id="4f10b-118">**Element**</span></span>|<span data-ttu-id="4f10b-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="4f10b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4f10b-120">Uri</span><span class="sxs-lookup"><span data-stu-id="4f10b-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="4f10b-121">包含指定.NET Framework 如何處理使用統一資源識別元 (Uri) 表示的 web 位址的設定。</span><span class="sxs-lookup"><span data-stu-id="4f10b-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f10b-122">備註</span><span class="sxs-lookup"><span data-stu-id="4f10b-122">Remarks</span></span>  
 <span data-ttu-id="4f10b-123">現有<xref:System.Uri>類別已擴充.NET Framework 3.5 中。</span><span class="sxs-lookup"><span data-stu-id="4f10b-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="4f10b-124">3.0 SP1 和 2.0 SP1 支援國際資源識別項 (IRI) 和國際化網域名稱 (IDN)。</span><span class="sxs-lookup"><span data-stu-id="4f10b-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="4f10b-125">目前的使用者不會看到任何變更從.NET Framework 2.0 的行為，除非它們特別啟用 IRI 和 IDN 支援。</span><span class="sxs-lookup"><span data-stu-id="4f10b-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="4f10b-126">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="4f10b-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4f10b-127">若要啟用 IRI 支援，下列兩項變更是必要的：</span><span class="sxs-lookup"><span data-stu-id="4f10b-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="4f10b-128">將下行新增至.NET Framework 2.0 目錄下的 machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="4f10b-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="4f10b-129">指定是否要國際化網域名稱 (IDN) 剖析套用至網域名稱以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="4f10b-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="4f10b-130">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="4f10b-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="4f10b-131">有三個可能的值進行 IDN 根據所使用的 DNS 伺服器：</span><span class="sxs-lookup"><span data-stu-id="4f10b-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="4f10b-132">啟用 idn = All</span><span class="sxs-lookup"><span data-stu-id="4f10b-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="4f10b-133">這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等名稱 （IDN 名稱）。</span><span class="sxs-lookup"><span data-stu-id="4f10b-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="4f10b-134">啟用 idn = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="4f10b-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="4f10b-135">這個值會轉換不是在本機的內部網路使用 Punycode 的對等名稱 （IDN 名稱） 上的所有 Unicode 網域名稱。</span><span class="sxs-lookup"><span data-stu-id="4f10b-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="4f10b-136">在此情況下，若要處理在本機的內部網路上的國際性名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。</span><span class="sxs-lookup"><span data-stu-id="4f10b-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="4f10b-137">啟用 idn = 無</span><span class="sxs-lookup"><span data-stu-id="4f10b-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="4f10b-138">此值不會轉換任何 Unicode 網域名稱，即可使用 Punycode。</span><span class="sxs-lookup"><span data-stu-id="4f10b-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="4f10b-139">這是預設值是與.NET Framework 2.0 行為一致。</span><span class="sxs-lookup"><span data-stu-id="4f10b-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="4f10b-140">啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。</span><span class="sxs-lookup"><span data-stu-id="4f10b-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="4f10b-141">Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。</span><span class="sxs-lookup"><span data-stu-id="4f10b-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="4f10b-142">這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。</span><span class="sxs-lookup"><span data-stu-id="4f10b-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="4f10b-143">組態檔</span><span class="sxs-lookup"><span data-stu-id="4f10b-143">Configuration Files</span></span>  
 <span data-ttu-id="4f10b-144">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="4f10b-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f10b-145">範例</span><span class="sxs-lookup"><span data-stu-id="4f10b-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4f10b-146">描述</span><span class="sxs-lookup"><span data-stu-id="4f10b-146">Description</span></span>  
 <span data-ttu-id="4f10b-147">下列範例顯示所使用的組態<xref:System.Uri>類別，以支援 IRI 剖析和 IDN 名稱。</span><span class="sxs-lookup"><span data-stu-id="4f10b-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4f10b-148">程式碼</span><span class="sxs-lookup"><span data-stu-id="4f10b-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f10b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f10b-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="4f10b-150">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4f10b-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
