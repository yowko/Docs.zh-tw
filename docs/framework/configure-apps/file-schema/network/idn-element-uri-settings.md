---
title: <idn> 項目 (URI 設定)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: f45922ecd5f7476362aab5348d91415d8e31c53f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195398"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="ca37a-102">\<idn> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="ca37a-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="ca37a-103">指定是否將國際化功能變數名稱 (IDN) 剖析套用至功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="ca37a-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="ca37a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca37a-104">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca37a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ca37a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ca37a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ca37a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca37a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ca37a-107">Attributes</span></span>  

|<span data-ttu-id="ca37a-108">**Element**</span><span class="sxs-lookup"><span data-stu-id="ca37a-108">**Element**</span></span>|<span data-ttu-id="ca37a-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="ca37a-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="ca37a-110">指定是否將「國際化功能變數名稱 (IDN) 剖析套用至功能變數名稱，預設值為「無」。</span><span class="sxs-lookup"><span data-stu-id="ca37a-110">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="ca37a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ca37a-111">Child elements</span></span>

<span data-ttu-id="ca37a-112">無</span><span class="sxs-lookup"><span data-stu-id="ca37a-112">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ca37a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ca37a-113">Parent elements</span></span>

|<span data-ttu-id="ca37a-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="ca37a-114">**Element**</span></span>|<span data-ttu-id="ca37a-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="ca37a-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ca37a-116">uri</span><span class="sxs-lookup"><span data-stu-id="ca37a-116">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="ca37a-117">包含的設定會指定 .NET Framework 如何處理使用統一資源識別項 (Uri) 所表示的 web 位址。</span><span class="sxs-lookup"><span data-stu-id="ca37a-117">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ca37a-118">備註</span><span class="sxs-lookup"><span data-stu-id="ca37a-118">Remarks</span></span>

<span data-ttu-id="ca37a-119">現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5 中擴充。</span><span class="sxs-lookup"><span data-stu-id="ca37a-119">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="ca37a-120">3.0 SP1 和 2.0 SP1，支援國際資源識別碼 (IRI) 和國際化功能變數名稱 (IDN) 。</span><span class="sxs-lookup"><span data-stu-id="ca37a-120">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="ca37a-121">除非使用者特別啟用 IRI 和 IDN 支援，否則目前的使用者不會看到 .NET Framework 2.0 行為的任何變更。</span><span class="sxs-lookup"><span data-stu-id="ca37a-121">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="ca37a-122">這可確保應用程式與舊版 .NET framework 相容。</span><span class="sxs-lookup"><span data-stu-id="ca37a-122">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="ca37a-123">若要啟用對 IRI 的支援，需要進行下列兩項變更：</span><span class="sxs-lookup"><span data-stu-id="ca37a-123">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="ca37a-124">將下列程式程式碼新增至 .NET Framework 2.0 目錄下的 machine.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="ca37a-124">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="ca37a-125">指定是否要將國際化功能變數名稱 (IDN) 剖析套用至功能變數名稱，以及是否應套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="ca37a-125">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="ca37a-126">此作業可在 machine.config 或 app.config 檔案中完成。</span><span class="sxs-lookup"><span data-stu-id="ca37a-126">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="ca37a-127">根據所使用的 DNS 伺服器，IDN 有三個可能的值：</span><span class="sxs-lookup"><span data-stu-id="ca37a-127">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="ca37a-128">已啟用 idn = 全部</span><span class="sxs-lookup"><span data-stu-id="ca37a-128">idn enabled = All</span></span>  

     <span data-ttu-id="ca37a-129">這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等名稱 (IDN 名稱)。</span><span class="sxs-lookup"><span data-stu-id="ca37a-129">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="ca37a-130">已啟用 idn = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="ca37a-130">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="ca37a-131">此值會將不在近端內部網路上的所有 Unicode 功能變數名稱轉換成使用 (IDN 名稱) 的 Punycode 對應專案。</span><span class="sxs-lookup"><span data-stu-id="ca37a-131">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="ca37a-132">在此情況下，若要處理近端內部網路上的國際名稱，用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。</span><span class="sxs-lookup"><span data-stu-id="ca37a-132">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="ca37a-133">已啟用 idn = 無</span><span class="sxs-lookup"><span data-stu-id="ca37a-133">idn enabled = None</span></span>

     <span data-ttu-id="ca37a-134">這個值不會轉換任何 Unicode 網域名稱即可使用 Punycode。</span><span class="sxs-lookup"><span data-stu-id="ca37a-134">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="ca37a-135">這是預設值，與 .NET Framework 2.0 的行為一致。</span><span class="sxs-lookup"><span data-stu-id="ca37a-135">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="ca37a-136">啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。</span><span class="sxs-lookup"><span data-stu-id="ca37a-136">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="ca37a-137">Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。</span><span class="sxs-lookup"><span data-stu-id="ca37a-137">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="ca37a-138">這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。</span><span class="sxs-lookup"><span data-stu-id="ca37a-138">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="ca37a-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="ca37a-139">Configuration files</span></span>

<span data-ttu-id="ca37a-140">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ca37a-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="ca37a-141">範例</span><span class="sxs-lookup"><span data-stu-id="ca37a-141">Example</span></span>

<span data-ttu-id="ca37a-142">下列範例顯示 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的設定：</span><span class="sxs-lookup"><span data-stu-id="ca37a-142">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ca37a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca37a-143">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="ca37a-144">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ca37a-144">Network Settings Schema</span></span>](index.md)
