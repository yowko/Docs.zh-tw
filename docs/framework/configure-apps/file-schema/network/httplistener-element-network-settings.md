---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 78526559164939667eab8848bc5fd2af6749d474
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195437"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="06bf2-102">\<httpListener> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="06bf2-102">\<httpListener> Element (Network Settings)</span></span>

<span data-ttu-id="06bf2-103">自訂類別使用的參數 <xref:System.Net.HttpListener> 。</span><span class="sxs-lookup"><span data-stu-id="06bf2-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="06bf2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="06bf2-104">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="06bf2-105">類型</span><span class="sxs-lookup"><span data-stu-id="06bf2-105">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06bf2-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="06bf2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="06bf2-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="06bf2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06bf2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="06bf2-108">Attributes</span></span>  
  
|<span data-ttu-id="06bf2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="06bf2-109">Attribute</span></span>|<span data-ttu-id="06bf2-110">描述</span><span class="sxs-lookup"><span data-stu-id="06bf2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06bf2-111">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="06bf2-111">unescapeRequestUrl</span></span>|<span data-ttu-id="06bf2-112">布林值，指出實例是否使用未經處理的 <xref:System.Net.HttpListener> 非轉義 uri，而不是已轉換的 uri。</span><span class="sxs-lookup"><span data-stu-id="06bf2-112">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06bf2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="06bf2-113">Child Elements</span></span>  

 <span data-ttu-id="06bf2-114">無。</span><span class="sxs-lookup"><span data-stu-id="06bf2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06bf2-115">父項目</span><span class="sxs-lookup"><span data-stu-id="06bf2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="06bf2-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="06bf2-116">**Element**</span></span>|<span data-ttu-id="06bf2-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="06bf2-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="06bf2-118">設定</span><span class="sxs-lookup"><span data-stu-id="06bf2-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="06bf2-119">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="06bf2-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06bf2-120">備註</span><span class="sxs-lookup"><span data-stu-id="06bf2-120">Remarks</span></span>  

 <span data-ttu-id="06bf2-121">**UnescapeRequestUrl**屬性會指出是否使用未經處理的非 <xref:System.Net.HttpListener> 轉義 uri，而不是轉換過的 uri，其中任何百分比編碼值都會轉換，並採用其他正規化步驟。</span><span class="sxs-lookup"><span data-stu-id="06bf2-121">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="06bf2-122">當 <xref:System.Net.HttpListener> 實例透過服務收到要求時 `http.sys` ，它會建立所提供之 URI 字串的實例 `http.sys` ，並將它公開為 <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="06bf2-122">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="06bf2-123">`http.sys`服務會公開兩個要求 URI 字串：</span><span class="sxs-lookup"><span data-stu-id="06bf2-123">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="06bf2-124">原始 URI</span><span class="sxs-lookup"><span data-stu-id="06bf2-124">Raw URI</span></span>  
  
- <span data-ttu-id="06bf2-125">已轉換的 URI</span><span class="sxs-lookup"><span data-stu-id="06bf2-125">Converted URI</span></span>  
  
 <span data-ttu-id="06bf2-126">原始 URI 是 <xref:System.Uri?displayProperty=nameWithType> 在 HTTP 要求的要求行中提供的：</span><span class="sxs-lookup"><span data-stu-id="06bf2-126">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="06bf2-127">`http.sys`針對上面所述的要求所提供的原始 URI 是 "/path/"。</span><span class="sxs-lookup"><span data-stu-id="06bf2-127">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="06bf2-128">這代表透過網路傳送 HTTP 動詞命令之後的字串。</span><span class="sxs-lookup"><span data-stu-id="06bf2-128">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="06bf2-129">`http.sys`服務會使用 HTTP 要求行中提供的 uri 和主機標頭來判斷要求應該轉送至的源伺服器，藉此從要求中提供的資訊建立已轉換的 uri。</span><span class="sxs-lookup"><span data-stu-id="06bf2-129">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="06bf2-130">這是藉由使用一組已註冊的 URI 前置詞來比較要求中的資訊來完成。</span><span class="sxs-lookup"><span data-stu-id="06bf2-130">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="06bf2-131">HTTP Server SDK 檔將這個已轉換的 URI 參考為 HTTP_COOKED_URL 結構。</span><span class="sxs-lookup"><span data-stu-id="06bf2-131">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="06bf2-132">為了能夠將要求與已註冊的 URI 前置詞進行比較，需要完成一些對要求的正規化。</span><span class="sxs-lookup"><span data-stu-id="06bf2-132">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="06bf2-133">針對上述範例，已轉換的 URI 如下所示：</span><span class="sxs-lookup"><span data-stu-id="06bf2-133">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="06bf2-134">服務會將 `http.sys` <xref:System.Uri.Host%2A?displayProperty=nameWithType> 屬性值和要求行中的字串結合，以建立已轉換的 URI。</span><span class="sxs-lookup"><span data-stu-id="06bf2-134">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="06bf2-135">此外， `http.sys` 此 <xref:System.Uri?displayProperty=nameWithType> 類別也會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="06bf2-135">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="06bf2-136">取消轉義所有百分比編碼的值。</span><span class="sxs-lookup"><span data-stu-id="06bf2-136">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="06bf2-137">將百分比編碼的非 ASCII 字元轉換成 UTF-16 字元標記法。</span><span class="sxs-lookup"><span data-stu-id="06bf2-137">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="06bf2-138">請注意，UTF-8 和 ANSI/DBCS 字元也支援 unicode 字元， (使用% uXXXX format) 的 Unicode 編碼。</span><span class="sxs-lookup"><span data-stu-id="06bf2-138">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="06bf2-139">執行其他正規化步驟，例如路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="06bf2-139">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="06bf2-140">因為要求未包含用於百分比編碼值之編碼的任何資訊，所以可能無法藉由剖析百分比編碼值來判斷正確的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="06bf2-140">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="06bf2-141">因此 `http.sys` ，提供兩個登錄機碼來修改進程：</span><span class="sxs-lookup"><span data-stu-id="06bf2-141">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="06bf2-142">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="06bf2-142">Registry Key</span></span>|<span data-ttu-id="06bf2-143">預設值</span><span class="sxs-lookup"><span data-stu-id="06bf2-143">Default Value</span></span>|<span data-ttu-id="06bf2-144">描述</span><span class="sxs-lookup"><span data-stu-id="06bf2-144">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="06bf2-145">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="06bf2-145">EnableNonUTF8</span></span>|<span data-ttu-id="06bf2-146">1</span><span class="sxs-lookup"><span data-stu-id="06bf2-146">1</span></span>|<span data-ttu-id="06bf2-147">如果為零，則 `http.sys` 只接受 utf-8 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="06bf2-147">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="06bf2-148">如果非零， `http.sys` 也會在要求中接受 ANSI 編碼或 DBCS 編碼的 url。</span><span class="sxs-lookup"><span data-stu-id="06bf2-148">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="06bf2-149">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="06bf2-149">FavorUTF8</span></span>|<span data-ttu-id="06bf2-150">1</span><span class="sxs-lookup"><span data-stu-id="06bf2-150">1</span></span>|<span data-ttu-id="06bf2-151">如果非零， `http.sys` 一律會嘗試將 URL 解碼為 utf-8; 如果轉換失敗，而且 EnableNonUTF8 不是零，Http.sys 接著會嘗試將它解碼為 ANSI 或 DBCS。</span><span class="sxs-lookup"><span data-stu-id="06bf2-151">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="06bf2-152">如果零 (，且 EnableNonUTF8 為非零) ，則會 `http.sys` 嘗試將它解碼為 ANSI 或 DBCS; 如果不成功，則會嘗試 utf-8 轉換。</span><span class="sxs-lookup"><span data-stu-id="06bf2-152">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="06bf2-153">當 <xref:System.Net.HttpListener> 收到要求時，它會使用已轉換的 URI `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="06bf2-153">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="06bf2-154">除了 Uri 中的字元和數位之外，還需要支援字元。</span><span class="sxs-lookup"><span data-stu-id="06bf2-154">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="06bf2-155">以下是用來抓取客戶編碼 "1/3812" 客戶資訊的 URI 範例：</span><span class="sxs-lookup"><span data-stu-id="06bf2-155">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="06bf2-156">請注意 Uri 中的百分比編碼斜線 (% 2F) 。</span><span class="sxs-lookup"><span data-stu-id="06bf2-156">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="06bf2-157">這是必要的，因為在此情況下，斜線字元代表資料，而不是路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="06bf2-157">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="06bf2-158">將字串傳遞至 Uri 的函式會導致下列 URI：</span><span class="sxs-lookup"><span data-stu-id="06bf2-158">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="06bf2-159">將路徑分割成其區段會導致下列元素：</span><span class="sxs-lookup"><span data-stu-id="06bf2-159">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="06bf2-160">這不是要求寄件者的意圖。</span><span class="sxs-lookup"><span data-stu-id="06bf2-160">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="06bf2-161">如果 **unescapeRequestUrl** 屬性設定為 **false**，則當 <xref:System.Net.HttpListener> 收到要求時，它會使用未經處理的 uri，而不是做為屬性的 `http.sys` 輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="06bf2-161">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="06bf2-162">**UnescapeRequestUrl**屬性的預設值為**true**。</span><span class="sxs-lookup"><span data-stu-id="06bf2-162">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="06bf2-163"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可以用來從適用的設定檔案取得**unescapeRequestUrl**屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="06bf2-163">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bf2-164">範例</span><span class="sxs-lookup"><span data-stu-id="06bf2-164">Example</span></span>  

 <span data-ttu-id="06bf2-165">下列範例將示範如何 <xref:System.Net.HttpListener> 在收到使用原始 uri 的要求時設定類別，而不使用轉換的 uri `http.sys` 做為屬性的輸入 <xref:System.Net.HttpListenerRequest.Url%2A> 。</span><span class="sxs-lookup"><span data-stu-id="06bf2-165">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="06bf2-166">項目資訊</span><span class="sxs-lookup"><span data-stu-id="06bf2-166">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="06bf2-167">命名空間</span><span class="sxs-lookup"><span data-stu-id="06bf2-167">Namespace</span></span>|<span data-ttu-id="06bf2-168">System.Net</span><span class="sxs-lookup"><span data-stu-id="06bf2-168">System.Net</span></span>|  
|<span data-ttu-id="06bf2-169">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="06bf2-169">Schema Name</span></span>||  
|<span data-ttu-id="06bf2-170">驗證檔</span><span class="sxs-lookup"><span data-stu-id="06bf2-170">Validation File</span></span>||  
|<span data-ttu-id="06bf2-171">可以是空的</span><span class="sxs-lookup"><span data-stu-id="06bf2-171">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="06bf2-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06bf2-172">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="06bf2-173">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="06bf2-173">Network Settings Schema</span></span>](index.md)
