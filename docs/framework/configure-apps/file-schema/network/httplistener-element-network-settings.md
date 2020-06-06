---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088381"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="b372d-102">\<httpListener> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b372d-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="b372d-103">自訂類別所使用的參數 <xref:System.Net.HttpListener> 。</span><span class="sxs-lookup"><span data-stu-id="b372d-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="b372d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b372d-104">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="b372d-105">類型</span><span class="sxs-lookup"><span data-stu-id="b372d-105">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b372d-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b372d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b372d-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b372d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b372d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="b372d-108">Attributes</span></span>  
  
|<span data-ttu-id="b372d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b372d-109">Attribute</span></span>|<span data-ttu-id="b372d-110">描述</span><span class="sxs-lookup"><span data-stu-id="b372d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b372d-111">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="b372d-111">unescapeRequestUrl</span></span>|<span data-ttu-id="b372d-112">布林值，指出實例是否使用未經處理的 <xref:System.Net.HttpListener> 非轉義 uri，而不是轉換後的 uri。</span><span class="sxs-lookup"><span data-stu-id="b372d-112">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b372d-113">子元素</span><span class="sxs-lookup"><span data-stu-id="b372d-113">Child Elements</span></span>  
 <span data-ttu-id="b372d-114">無。</span><span class="sxs-lookup"><span data-stu-id="b372d-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b372d-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b372d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b372d-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="b372d-116">**Element**</span></span>|<span data-ttu-id="b372d-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="b372d-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b372d-118">設定</span><span class="sxs-lookup"><span data-stu-id="b372d-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b372d-119">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="b372d-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b372d-120">備註</span><span class="sxs-lookup"><span data-stu-id="b372d-120">Remarks</span></span>  
 <span data-ttu-id="b372d-121">**UnescapeRequestUrl**屬性會指出是否使用未經處理的非 <xref:System.Net.HttpListener> 轉義 uri，而不是轉換的 uri，其中會轉換任何百分比編碼的值，並採用其他正規化步驟。</span><span class="sxs-lookup"><span data-stu-id="b372d-121">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="b372d-122">當 <xref:System.Net.HttpListener> 實例透過服務收到要求時 `http.sys` ，它會建立所提供之 URI 字串的實例 `http.sys` ，並將它公開為 <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b372d-122">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b372d-123">`http.sys`服務會公開兩個要求 URI 字串：</span><span class="sxs-lookup"><span data-stu-id="b372d-123">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="b372d-124">原始 URI</span><span class="sxs-lookup"><span data-stu-id="b372d-124">Raw URI</span></span>  
  
- <span data-ttu-id="b372d-125">已轉換 URI</span><span class="sxs-lookup"><span data-stu-id="b372d-125">Converted URI</span></span>  
  
 <span data-ttu-id="b372d-126">原始 URI 是 <xref:System.Uri?displayProperty=nameWithType> HTTP 要求的要求行中所提供的：</span><span class="sxs-lookup"><span data-stu-id="b372d-126">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="b372d-127">`http.sys`針對上面所述的要求所提供的原始 URI 是 "/path/"。</span><span class="sxs-lookup"><span data-stu-id="b372d-127">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="b372d-128">這代表在透過網路傳送的 HTTP 動詞命令之後的字串。</span><span class="sxs-lookup"><span data-stu-id="b372d-128">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="b372d-129">`http.sys`服務會從要求中提供的資訊建立已轉換的 uri，方法是使用 HTTP 要求行中提供的 URI 和主機標頭來判斷要求應轉送至的源伺服器。</span><span class="sxs-lookup"><span data-stu-id="b372d-129">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="b372d-130">這是藉由比較要求中的資訊與一組已註冊的 URI 前置詞來完成。</span><span class="sxs-lookup"><span data-stu-id="b372d-130">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="b372d-131">HTTP 伺服器 SDK 檔是指此轉換的 URI 做為 HTTP_COOKED_URL 結構。</span><span class="sxs-lookup"><span data-stu-id="b372d-131">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="b372d-132">為了能夠比較要求與已註冊的 URI 前置詞，需要對要求進行一些正規化。</span><span class="sxs-lookup"><span data-stu-id="b372d-132">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="b372d-133">針對上述範例，轉換後的 URI 如下所示：</span><span class="sxs-lookup"><span data-stu-id="b372d-133">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="b372d-134">服務會將 `http.sys` <xref:System.Uri.Host%2A?displayProperty=nameWithType> 屬性值和要求行中的字串結合，以建立已轉換的 URI。</span><span class="sxs-lookup"><span data-stu-id="b372d-134">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="b372d-135">此外， `http.sys` 和 <xref:System.Uri?displayProperty=nameWithType> 類別也會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b372d-135">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="b372d-136">取消轉義所有百分比編碼的值。</span><span class="sxs-lookup"><span data-stu-id="b372d-136">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="b372d-137">將百分比編碼的非 ASCII 字元轉換成 UTF-16 字元標記法。</span><span class="sxs-lookup"><span data-stu-id="b372d-137">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="b372d-138">請注意，支援 UTF-8 和 ANSI/DBCS 字元，以及 Unicode 字元（使用% uXXXX 格式的 Unicode 編碼）。</span><span class="sxs-lookup"><span data-stu-id="b372d-138">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="b372d-139">執行其他正規化步驟，例如路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="b372d-139">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="b372d-140">由於要求並未包含用於百分比編碼值之編碼的任何相關資訊，因此您可能無法藉由剖析百分比編碼的值來判斷正確的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b372d-140">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="b372d-141">因此 `http.sys` ，會提供兩個登錄機碼來修改進程：</span><span class="sxs-lookup"><span data-stu-id="b372d-141">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="b372d-142">登錄金鑰</span><span class="sxs-lookup"><span data-stu-id="b372d-142">Registry Key</span></span>|<span data-ttu-id="b372d-143">預設值</span><span class="sxs-lookup"><span data-stu-id="b372d-143">Default Value</span></span>|<span data-ttu-id="b372d-144">描述</span><span class="sxs-lookup"><span data-stu-id="b372d-144">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="b372d-145">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="b372d-145">EnableNonUTF8</span></span>|<span data-ttu-id="b372d-146">1</span><span class="sxs-lookup"><span data-stu-id="b372d-146">1</span></span>|<span data-ttu-id="b372d-147">如果為零，則 `http.sys` 只接受 utf-8 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="b372d-147">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="b372d-148">如果不是零， `http.sys` 也會在要求中接受 ANSI 編碼或 DBCS 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="b372d-148">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="b372d-149">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="b372d-149">FavorUTF8</span></span>|<span data-ttu-id="b372d-150">1</span><span class="sxs-lookup"><span data-stu-id="b372d-150">1</span></span>|<span data-ttu-id="b372d-151">如果不是零， `http.sys` 一律會先嘗試將 URL 解碼為 utf-8; 如果該轉換失敗且 EnableNonUTF8 為非零，則 HTTP.sys 會嘗試將它解碼為 ANSI 或 DBCS。</span><span class="sxs-lookup"><span data-stu-id="b372d-151">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="b372d-152">如果為零（且 EnableNonUTF8 為非零），會 `http.sys` 嘗試將它解碼為 ANSI 或 DBCS; 如果不成功，則會嘗試 utf-8 轉換。</span><span class="sxs-lookup"><span data-stu-id="b372d-152">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="b372d-153">當 <xref:System.Net.HttpListener> 收到要求時，它會使用已轉換的 URI `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b372d-153">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="b372d-154">除了 Uri 中的字元和數位以外，還需要支援字元。</span><span class="sxs-lookup"><span data-stu-id="b372d-154">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="b372d-155">範例是下列 URI，用來抓取客戶編碼 "1/3812" 的客戶資訊：</span><span class="sxs-lookup"><span data-stu-id="b372d-155">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="b372d-156">請注意 Uri 中的百分比編碼斜線（% 2F）。</span><span class="sxs-lookup"><span data-stu-id="b372d-156">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="b372d-157">這是必要的，因為在此情況下，斜線字元代表資料，而不是路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b372d-157">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="b372d-158">將字串傳遞至 Uri 的函式會導致下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b372d-158">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="b372d-159">將路徑分割成其區段會產生下列元素：</span><span class="sxs-lookup"><span data-stu-id="b372d-159">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="b372d-160">這不是要求寄件者的意圖。</span><span class="sxs-lookup"><span data-stu-id="b372d-160">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="b372d-161">如果**unescapeRequestUrl**屬性設定為**false**，則當 <xref:System.Net.HttpListener> 收到要求時，它會使用原始的 uri，而不是所轉換的 uri `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b372d-161">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="b372d-162">**UnescapeRequestUrl**屬性的預設值為**true**。</span><span class="sxs-lookup"><span data-stu-id="b372d-162">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="b372d-163"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可以用來從適用的設定檔中取得**unescapeRequestUrl**屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="b372d-163">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b372d-164">範例</span><span class="sxs-lookup"><span data-stu-id="b372d-164">Example</span></span>  
 <span data-ttu-id="b372d-165">下列範例示範如何在 <xref:System.Net.HttpListener> 接收到要求時，使用未經處理的 uri （而不是轉換的 uri）做為屬性的輸入，來設定類別 `http.sys` <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b372d-165">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="b372d-166">項目資訊</span><span class="sxs-lookup"><span data-stu-id="b372d-166">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="b372d-167">命名空間</span><span class="sxs-lookup"><span data-stu-id="b372d-167">Namespace</span></span>|<span data-ttu-id="b372d-168">System.Net</span><span class="sxs-lookup"><span data-stu-id="b372d-168">System.Net</span></span>|  
|<span data-ttu-id="b372d-169">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="b372d-169">Schema Name</span></span>||  
|<span data-ttu-id="b372d-170">驗證檔</span><span class="sxs-lookup"><span data-stu-id="b372d-170">Validation File</span></span>||  
|<span data-ttu-id="b372d-171">可以是空的</span><span class="sxs-lookup"><span data-stu-id="b372d-171">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="b372d-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b372d-172">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="b372d-173">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b372d-173">Network Settings Schema</span></span>](index.md)
