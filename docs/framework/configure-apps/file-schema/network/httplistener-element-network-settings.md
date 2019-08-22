---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: cb24dc7296e2f2f6ea292566330d3d6ae4f25f85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664132"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="0ebe2-102">\<HTTPListener > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0ebe2-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="0ebe2-103">自訂類別所<xref:System.Net.HttpListener>使用的參數。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="0ebe2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0ebe2-104">\<configuration></span></span>  
<span data-ttu-id="0ebe2-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0ebe2-105">\<system.net></span></span>  
<span data-ttu-id="0ebe2-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="0ebe2-106">\<settings></span></span>  
<span data-ttu-id="0ebe2-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="0ebe2-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebe2-108">語法</span><span class="sxs-lookup"><span data-stu-id="0ebe2-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="0ebe2-109">類型</span><span class="sxs-lookup"><span data-stu-id="0ebe2-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ebe2-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ebe2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0ebe2-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ebe2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0ebe2-112">Attributes</span></span>  
  
|<span data-ttu-id="0ebe2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0ebe2-113">Attribute</span></span>|<span data-ttu-id="0ebe2-114">說明</span><span class="sxs-lookup"><span data-stu-id="0ebe2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0ebe2-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="0ebe2-115">unescapeRequestUrl</span></span>|<span data-ttu-id="0ebe2-116">布林值, 指出<xref:System.Net.HttpListener>實例是否使用未經處理的非轉義 uri, 而不是轉換後的 uri。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ebe2-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0ebe2-117">Child Elements</span></span>  
 <span data-ttu-id="0ebe2-118">無。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ebe2-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0ebe2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0ebe2-120">**目**</span><span class="sxs-lookup"><span data-stu-id="0ebe2-120">**Element**</span></span>|<span data-ttu-id="0ebe2-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="0ebe2-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0ebe2-122">設置</span><span class="sxs-lookup"><span data-stu-id="0ebe2-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="0ebe2-123">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebe2-124">備註</span><span class="sxs-lookup"><span data-stu-id="0ebe2-124">Remarks</span></span>  
 <span data-ttu-id="0ebe2-125">**UnescapeRequestUrl**屬性會指出是否<xref:System.Net.HttpListener>使用未經處理的非轉義 uri, 而不是轉換的 uri, 其中會轉換任何百分比編碼的值, 並採用其他正規化步驟。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="0ebe2-126">當實例透過服務收到要求時, 它會建立`http.sys`所提供之 URI 字串的實例, 並將它公開為<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>屬性。 `http.sys` <xref:System.Net.HttpListener></span><span class="sxs-lookup"><span data-stu-id="0ebe2-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="0ebe2-127">`http.sys`服務會公開兩個要求 URI 字串:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="0ebe2-128">原始 URI</span><span class="sxs-lookup"><span data-stu-id="0ebe2-128">Raw URI</span></span>  
  
- <span data-ttu-id="0ebe2-129">已轉換 URI</span><span class="sxs-lookup"><span data-stu-id="0ebe2-129">Converted URI</span></span>  
  
 <span data-ttu-id="0ebe2-130">原始 URI 是 HTTP 要求<xref:System.Uri?displayProperty=nameWithType>的要求行中所提供的:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="0ebe2-131">`http.sys`針對上面所述的要求所提供的原始 URI 是 "/path/"。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="0ebe2-132">這代表在透過網路傳送的 HTTP 動詞命令之後的字串。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="0ebe2-133">`http.sys`服務會從要求中提供的資訊建立已轉換的 uri, 方法是使用 HTTP 要求行中提供的 URI 和主機標頭來判斷要求應轉送至的源伺服器。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="0ebe2-134">這是藉由比較要求中的資訊與一組已註冊的 URI 前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="0ebe2-135">HTTP 伺服器 SDK 檔是指此轉換後的 URI 做為 HTTP_COOKED_URL 結構。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="0ebe2-136">為了能夠比較要求與已註冊的 URI 前置詞, 需要對要求進行一些正規化。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="0ebe2-137">針對上述範例, 轉換後的 URI 如下所示:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="0ebe2-138">服務會將<xref:System.Uri.Host%2A?displayProperty=nameWithType>屬性值和要求行中的字串結合, 以建立已轉換的 URI。 `http.sys`</span><span class="sxs-lookup"><span data-stu-id="0ebe2-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="0ebe2-139">此外, `http.sys` <xref:System.Uri?displayProperty=nameWithType>和類別也會執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="0ebe2-140">取消轉義所有百分比編碼的值。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="0ebe2-141">將百分比編碼的非 ASCII 字元轉換成 UTF-16 字元標記法。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="0ebe2-142">請注意, 支援 UTF-8 和 ANSI/DBCS 字元, 以及 Unicode 字元 (使用% uXXXX 格式的 Unicode 編碼)。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="0ebe2-143">執行其他正規化步驟, 例如路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="0ebe2-144">由於要求並未包含用於百分比編碼值之編碼的任何相關資訊, 因此您可能無法藉由剖析百分比編碼的值來判斷正確的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="0ebe2-145">因此`http.sys` , 會提供兩個登錄機碼來修改進程:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="0ebe2-146">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="0ebe2-146">Registry Key</span></span>|<span data-ttu-id="0ebe2-147">預設值</span><span class="sxs-lookup"><span data-stu-id="0ebe2-147">Default Value</span></span>|<span data-ttu-id="0ebe2-148">描述</span><span class="sxs-lookup"><span data-stu-id="0ebe2-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="0ebe2-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="0ebe2-149">EnableNonUTF8</span></span>|<span data-ttu-id="0ebe2-150">1</span><span class="sxs-lookup"><span data-stu-id="0ebe2-150">1</span></span>|<span data-ttu-id="0ebe2-151">如果為零`http.sys` , 則只接受 utf-8 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="0ebe2-152">如果不是零, `http.sys`也會在要求中接受 ANSI 編碼或 DBCS 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="0ebe2-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="0ebe2-153">FavorUTF8</span></span>|<span data-ttu-id="0ebe2-154">1</span><span class="sxs-lookup"><span data-stu-id="0ebe2-154">1</span></span>|<span data-ttu-id="0ebe2-155">如果不是零, `http.sys`一律會先嘗試將 URL 解碼為 utf-8; 如果該轉換失敗且 EnableNonUTF8 為非零, 則 HTTP.sys 會嘗試將它解碼為 ANSI 或 DBCS。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="0ebe2-156">如果為零 (且 EnableNonUTF8 為非零), `http.sys`會嘗試將它解碼為 ANSI 或 DBCS; 如果不成功, 則會嘗試 utf-8 轉換。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="0ebe2-157">當<xref:System.Net.HttpListener>收到要求時, 它會使用已轉換的`http.sys` URI 做為<xref:System.Net.HttpListenerRequest.Url%2A>屬性的輸入。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="0ebe2-158">除了 Uri 中的字元和數位以外, 還需要支援字元。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="0ebe2-159">範例是下列 URI, 用來抓取客戶編碼 "1/3812" 的客戶資訊:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="0ebe2-160">請注意 Uri 中的百分比編碼斜線 (% 2F)。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="0ebe2-161">這是必要的, 因為在此情況下, 斜線字元代表資料, 而不是路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="0ebe2-162">將字串傳遞至 Uri 的函式會導致下列 URI:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="0ebe2-163">將路徑分割成其區段會產生下列元素:</span><span class="sxs-lookup"><span data-stu-id="0ebe2-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="0ebe2-164">這不是要求寄件者的意圖。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="0ebe2-165">如果**unescapeRequestUrl**屬性設定為**false**, 則當<xref:System.Net.HttpListener>收到要求時, 它會使用原始的 uri, `http.sys`而不是所轉換的<xref:System.Net.HttpListenerRequest.Url%2A> uri 做為屬性的輸入。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="0ebe2-166">**UnescapeRequestUrl**屬性的預設值為**true**。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="0ebe2-167">屬性可以用來從適用的設定檔中取得 unescapeRequestUrl 屬性的目前值。 <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A></span><span class="sxs-lookup"><span data-stu-id="0ebe2-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ebe2-168">範例</span><span class="sxs-lookup"><span data-stu-id="0ebe2-168">Example</span></span>  
 <span data-ttu-id="0ebe2-169">下列範例示範如何在接收到要求<xref:System.Net.HttpListener>時, 使用未經處理的 uri (而不是轉換的`http.sys` uri) 做為<xref:System.Net.HttpListenerRequest.Url%2A>屬性的輸入, 來設定類別。</span><span class="sxs-lookup"><span data-stu-id="0ebe2-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="0ebe2-170">項目資訊</span><span class="sxs-lookup"><span data-stu-id="0ebe2-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="0ebe2-171">命名空間</span><span class="sxs-lookup"><span data-stu-id="0ebe2-171">Namespace</span></span>|<span data-ttu-id="0ebe2-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="0ebe2-172">System.Net</span></span>|  
|<span data-ttu-id="0ebe2-173">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="0ebe2-173">Schema Name</span></span>||  
|<span data-ttu-id="0ebe2-174">驗證檔</span><span class="sxs-lookup"><span data-stu-id="0ebe2-174">Validation File</span></span>||  
|<span data-ttu-id="0ebe2-175">可以是空的</span><span class="sxs-lookup"><span data-stu-id="0ebe2-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0ebe2-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ebe2-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="0ebe2-177">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0ebe2-177">Network Settings Schema</span></span>](index.md)
