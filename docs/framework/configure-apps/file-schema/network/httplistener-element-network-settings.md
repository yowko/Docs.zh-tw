---
title: "&lt;httpListener&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a><span data-ttu-id="a4085-102">&lt;httpListener&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="a4085-102">&lt;httpListener&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a4085-103">自訂所用參數<xref:System.Net.HttpListener>類別。</span><span class="sxs-lookup"><span data-stu-id="a4085-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="a4085-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a4085-104">\<configuration></span></span>  
<span data-ttu-id="a4085-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="a4085-105">\<system.net></span></span>  
<span data-ttu-id="a4085-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="a4085-106">\<settings></span></span>  
<span data-ttu-id="a4085-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="a4085-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4085-108">語法</span><span class="sxs-lookup"><span data-stu-id="a4085-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="a4085-109">類型</span><span class="sxs-lookup"><span data-stu-id="a4085-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4085-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a4085-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a4085-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a4085-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4085-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a4085-112">Attributes</span></span>  
  
|<span data-ttu-id="a4085-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a4085-113">Attribute</span></span>|<span data-ttu-id="a4085-114">描述</span><span class="sxs-lookup"><span data-stu-id="a4085-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a4085-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="a4085-115">unescapeRequestUrl</span></span>|<span data-ttu-id="a4085-116">布林值，指出如果<xref:System.Net.HttpListener>執行個體會使用原始的未逸出的 URI，而不是轉換後的 URI。</span><span class="sxs-lookup"><span data-stu-id="a4085-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4085-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a4085-117">Child Elements</span></span>  
 <span data-ttu-id="a4085-118">無。</span><span class="sxs-lookup"><span data-stu-id="a4085-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4085-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a4085-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a4085-120">**目**</span><span class="sxs-lookup"><span data-stu-id="a4085-120">**Element**</span></span>|<span data-ttu-id="a4085-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="a4085-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a4085-122">設定</span><span class="sxs-lookup"><span data-stu-id="a4085-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="a4085-123">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="a4085-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4085-124">備註</span><span class="sxs-lookup"><span data-stu-id="a4085-124">Remarks</span></span>  
 <span data-ttu-id="a4085-125">**UnescapeRequestUrl**屬性會指出如果<xref:System.Net.HttpListener>而不是轉換後的 URI 轉換百分比編碼的任何值，會採取其他的正規化步驟會使用原始的未逸出的 URI。</span><span class="sxs-lookup"><span data-stu-id="a4085-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="a4085-126">當<xref:System.Net.HttpListener>執行個體收到要求時透過`http.sys`服務，它會建立所提供的 URI 字串的執行個體`http.sys`，並公開其為<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="a4085-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a4085-127">`http.sys`服務會公開兩個要求 URI 字串：</span><span class="sxs-lookup"><span data-stu-id="a4085-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="a4085-128">未經處理的 URI</span><span class="sxs-lookup"><span data-stu-id="a4085-128">Raw URI</span></span>  
  
-   <span data-ttu-id="a4085-129">已轉換的 URI</span><span class="sxs-lookup"><span data-stu-id="a4085-129">Converted URI</span></span>  
  
 <span data-ttu-id="a4085-130">未經處理的 URI 是<xref:System.Uri?displayProperty=nameWithType>提供 HTTP 要求的要求行中：</span><span class="sxs-lookup"><span data-stu-id="a4085-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="a4085-131">所提供的原始 URI`http.sys`上面所提的要求是"/ 路徑 /"。</span><span class="sxs-lookup"><span data-stu-id="a4085-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="a4085-132">這表示它已透過網路傳送接下來的 HTTP 動詞命令的字串。</span><span class="sxs-lookup"><span data-stu-id="a4085-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="a4085-133">`http.sys`服務會使用 HTTP 要求行中所提供的 URI，在要求中所提供的資訊來建立已轉換的 URI 和主機標頭，以判斷原始伺服器的要求應該會轉送到。</span><span class="sxs-lookup"><span data-stu-id="a4085-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="a4085-134">這是藉由比較一組已註冊的 URI 前置詞的要求中的資訊。</span><span class="sxs-lookup"><span data-stu-id="a4085-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="a4085-135">HTTP 伺服器 SDK 文件指 HTTP_COOKED_URL 結構為此轉換的 URI。</span><span class="sxs-lookup"><span data-stu-id="a4085-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="a4085-136">為了要比較的要求已註冊的 URI 前置詞，需要執行某些要求的正規化。</span><span class="sxs-lookup"><span data-stu-id="a4085-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="a4085-137">轉換 URI 上述範例應如下：</span><span class="sxs-lookup"><span data-stu-id="a4085-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="a4085-138">`http.sys`服務結合<xref:System.Uri.Host%2A?displayProperty=nameWithType>屬性值，並要求條線建立轉換的 URI 中的字串。</span><span class="sxs-lookup"><span data-stu-id="a4085-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="a4085-139">此外，`http.sys`和<xref:System.Uri?displayProperty=nameWithType>類別也會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="a4085-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="a4085-140">取消-逸出所有百分比編碼值。</span><span class="sxs-lookup"><span data-stu-id="a4085-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="a4085-141">轉換百分比編碼為 utf-16 字元表示法的非 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="a4085-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="a4085-142">請注意，utf-8 與 ANSI/DBCS 字元支援以及 Unicode 字元 （Unicode 編碼使用 %uxxxx 格式）。</span><span class="sxs-lookup"><span data-stu-id="a4085-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="a4085-143">執行其他的正規化步驟，例如路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="a4085-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="a4085-144">要求不包含任何百分比編碼值使用的編碼方式相關資訊，因為它可能無法判斷正確的編碼方式只是藉由剖析的百分比編碼值。</span><span class="sxs-lookup"><span data-stu-id="a4085-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="a4085-145">因此`http.sys`提供修改程序的兩個登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="a4085-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="a4085-146">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="a4085-146">Registry Key</span></span>|<span data-ttu-id="a4085-147">預設值</span><span class="sxs-lookup"><span data-stu-id="a4085-147">Default Value</span></span>|<span data-ttu-id="a4085-148">描述</span><span class="sxs-lookup"><span data-stu-id="a4085-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="a4085-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="a4085-149">EnableNonUTF8</span></span>|<span data-ttu-id="a4085-150">1</span><span class="sxs-lookup"><span data-stu-id="a4085-150">1</span></span>|<span data-ttu-id="a4085-151">如果是零，`http.sys`接受只有 UTF 8 編碼的 Url。</span><span class="sxs-lookup"><span data-stu-id="a4085-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="a4085-152">如果不是零，`http.sys`也接受 ANSI 編碼或 DBCS 編碼在要求中的 Url。</span><span class="sxs-lookup"><span data-stu-id="a4085-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="a4085-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="a4085-153">FavorUTF8</span></span>|<span data-ttu-id="a4085-154">1</span><span class="sxs-lookup"><span data-stu-id="a4085-154">1</span></span>|<span data-ttu-id="a4085-155">如果不是零，`http.sys`一律會嘗試解碼 URL 為 utf-8 第一次。 如果該轉換失敗，而且 EnableNonUTF8 為非零，Http.sys，然後嘗試將它解碼為 ANSI 或依 DBCS。</span><span class="sxs-lookup"><span data-stu-id="a4085-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="a4085-156">如果是零 （和 EnableNonUTF8 為非零），`http.sys`嘗試將它解碼為 ANSI 或依 DBCS; 如果不成功，它會嘗試 utf-8 轉換。</span><span class="sxs-lookup"><span data-stu-id="a4085-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="a4085-157">當<xref:System.Net.HttpListener>收到要求時，它會使用轉換的 URI 從`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a4085-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="a4085-158">沒有需要支援在 Uri 中的字元和數字以外的字元。</span><span class="sxs-lookup"><span data-stu-id="a4085-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="a4085-159">範例是下列的 URI 用來擷取客戶的客戶資訊數字"1/3812":</span><span class="sxs-lookup"><span data-stu-id="a4085-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="a4085-160">請注意百分比編碼中的斜線的 Uri (%2f)。</span><span class="sxs-lookup"><span data-stu-id="a4085-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="a4085-161">必須這樣做，因為在此情況下的斜線字元表示的資料，不是路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="a4085-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="a4085-162">將字串傳遞至 Uri 建構函式會導致下列 URI:</span><span class="sxs-lookup"><span data-stu-id="a4085-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="a4085-163">分割為其區段路徑會產生下列項目：</span><span class="sxs-lookup"><span data-stu-id="a4085-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="a4085-164">這不是寄件者要求的意圖。</span><span class="sxs-lookup"><span data-stu-id="a4085-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="a4085-165">如果**unescapeRequestUrl**屬性設為**false**，則當<xref:System.Net.HttpListener>收到要求時，它會使用原始 URI，而不是從轉換過的 URI`http.sys`做為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a4085-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="a4085-166">預設值為**unescapeRequestUrl**屬性是**true**。</span><span class="sxs-lookup"><span data-stu-id="a4085-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="a4085-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可以用來取得目前的值**unescapeRequestUrl**適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="a4085-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4085-168">範例</span><span class="sxs-lookup"><span data-stu-id="a4085-168">Example</span></span>  
 <span data-ttu-id="a4085-169">下列範例示範如何設定<xref:System.Net.HttpListener>類別當它收到要求時使用原始 URI，而不是從轉換過的 URI`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a4085-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="a4085-170">項目資訊</span><span class="sxs-lookup"><span data-stu-id="a4085-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="a4085-171">命名空間</span><span class="sxs-lookup"><span data-stu-id="a4085-171">Namespace</span></span>|<span data-ttu-id="a4085-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="a4085-172">System.Net</span></span>|  
|<span data-ttu-id="a4085-173">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="a4085-173">Schema Name</span></span>||  
|<span data-ttu-id="a4085-174">驗證檔</span><span class="sxs-lookup"><span data-stu-id="a4085-174">Validation File</span></span>||  
|<span data-ttu-id="a4085-175">可以是空白</span><span class="sxs-lookup"><span data-stu-id="a4085-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="a4085-176">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4085-176">See Also</span></span>  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [<span data-ttu-id="a4085-177">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a4085-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
