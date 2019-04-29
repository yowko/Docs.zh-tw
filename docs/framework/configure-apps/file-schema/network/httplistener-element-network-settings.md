---
title: <httpListener> 項目 (網路設定)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705073"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="1758d-102">\<httpListener > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="1758d-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="1758d-103">自訂所使用的參數<xref:System.Net.HttpListener>類別。</span><span class="sxs-lookup"><span data-stu-id="1758d-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="1758d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1758d-104">\<configuration></span></span>  
<span data-ttu-id="1758d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1758d-105">\<system.net></span></span>  
<span data-ttu-id="1758d-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="1758d-106">\<settings></span></span>  
<span data-ttu-id="1758d-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="1758d-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1758d-108">語法</span><span class="sxs-lookup"><span data-stu-id="1758d-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="1758d-109">類型</span><span class="sxs-lookup"><span data-stu-id="1758d-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1758d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1758d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1758d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1758d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1758d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1758d-112">Attributes</span></span>  
  
|<span data-ttu-id="1758d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1758d-113">Attribute</span></span>|<span data-ttu-id="1758d-114">描述</span><span class="sxs-lookup"><span data-stu-id="1758d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1758d-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="1758d-115">unescapeRequestUrl</span></span>|<span data-ttu-id="1758d-116">布林值，指出如果<xref:System.Net.HttpListener>執行個體會使用原始未逸出的 URI，而不是轉換的 URI。</span><span class="sxs-lookup"><span data-stu-id="1758d-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1758d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1758d-117">Child Elements</span></span>  
 <span data-ttu-id="1758d-118">無。</span><span class="sxs-lookup"><span data-stu-id="1758d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1758d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1758d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1758d-120">**目**</span><span class="sxs-lookup"><span data-stu-id="1758d-120">**Element**</span></span>|<span data-ttu-id="1758d-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="1758d-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1758d-122">settings</span><span class="sxs-lookup"><span data-stu-id="1758d-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="1758d-123">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="1758d-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1758d-124">備註</span><span class="sxs-lookup"><span data-stu-id="1758d-124">Remarks</span></span>  
 <span data-ttu-id="1758d-125">**UnescapeRequestUrl**屬性會指出如果<xref:System.Net.HttpListener>使用原始未逸出的 URI，而不是轉換的 URI，其中任何百分比編碼的值會轉換，並且會採取其他的正規化步驟。</span><span class="sxs-lookup"><span data-stu-id="1758d-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="1758d-126">當<xref:System.Net.HttpListener>執行個體收到的要求，透過`http.sys`服務，它會建立所提供的 URI 字串的執行個體`http.sys`，並公開為<xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="1758d-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="1758d-127">`http.sys`服務會公開兩個要求的 URI 字串：</span><span class="sxs-lookup"><span data-stu-id="1758d-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="1758d-128">原始 URI</span><span class="sxs-lookup"><span data-stu-id="1758d-128">Raw URI</span></span>  
  
- <span data-ttu-id="1758d-129">轉換的 URI</span><span class="sxs-lookup"><span data-stu-id="1758d-129">Converted URI</span></span>  
  
 <span data-ttu-id="1758d-130">未經處理的 URI 是<xref:System.Uri?displayProperty=nameWithType>HTTP 要求的要求行中提供：</span><span class="sxs-lookup"><span data-stu-id="1758d-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="1758d-131">所提供的原始 URI`http.sys`前面所述，此要求是"/ 路徑 /"。</span><span class="sxs-lookup"><span data-stu-id="1758d-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="1758d-132">這表示透過網路傳送下列 HTTP 動詞命令的字串。</span><span class="sxs-lookup"><span data-stu-id="1758d-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="1758d-133">`http.sys`服務會使用 HTTP 要求行中所提供的 URI 要求中所提供的資訊來建立轉換的 URI 和主機標頭，以判斷原始伺服器要求應該轉送到。</span><span class="sxs-lookup"><span data-stu-id="1758d-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="1758d-134">這是藉由比較從已註冊的 URI 前置詞的一組與要求的資訊。</span><span class="sxs-lookup"><span data-stu-id="1758d-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="1758d-135">HTTP 伺服器 SDK 文件會將稱為 HTTP_COOKED_URL 結構的這個轉換的 URI。</span><span class="sxs-lookup"><span data-stu-id="1758d-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="1758d-136">為了能夠比較要求，並已註冊的 URI 前置詞，要求一些正規化必須完成。</span><span class="sxs-lookup"><span data-stu-id="1758d-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="1758d-137">上述轉換的 URI 範例會是，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1758d-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="1758d-138">`http.sys`服務結合了<xref:System.Uri.Host%2A?displayProperty=nameWithType>屬性值，並建立轉換的 URI 要求行中的字串。</span><span class="sxs-lookup"><span data-stu-id="1758d-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="1758d-139">颾魤 ㄛ`http.sys`而<xref:System.Uri?displayProperty=nameWithType>類別也會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="1758d-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="1758d-140">取消-逸出所有百分比編碼的值。</span><span class="sxs-lookup"><span data-stu-id="1758d-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="1758d-141">將百分比編碼為 utf-16 字元表示法的非 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="1758d-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="1758d-142">請注意，Unicode 字元 （Unicode 編碼使用 %uxxxx 格式） 以及支援 utf-8 和 ANSI/DBCS 字元。</span><span class="sxs-lookup"><span data-stu-id="1758d-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="1758d-143">執行其他的正規化步驟，例如路徑壓縮。</span><span class="sxs-lookup"><span data-stu-id="1758d-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="1758d-144">因為要求未包含任何百分比編碼的值使用的編碼方式相關資訊，它可能無法判斷正確的編碼方式，就只是藉由剖析的百分比編碼的值。</span><span class="sxs-lookup"><span data-stu-id="1758d-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="1758d-145">因此`http.sys`提供兩個登錄機碼修改程序：</span><span class="sxs-lookup"><span data-stu-id="1758d-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="1758d-146">登錄機碼</span><span class="sxs-lookup"><span data-stu-id="1758d-146">Registry Key</span></span>|<span data-ttu-id="1758d-147">預設值</span><span class="sxs-lookup"><span data-stu-id="1758d-147">Default Value</span></span>|<span data-ttu-id="1758d-148">描述</span><span class="sxs-lookup"><span data-stu-id="1758d-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="1758d-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="1758d-149">EnableNonUTF8</span></span>|<span data-ttu-id="1758d-150">1</span><span class="sxs-lookup"><span data-stu-id="1758d-150">1</span></span>|<span data-ttu-id="1758d-151">如果是零，`http.sys`接受僅 UTF-8 編碼的 Url。</span><span class="sxs-lookup"><span data-stu-id="1758d-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="1758d-152">如果不是零，`http.sys`也接受 ANSI 編碼或 DBCS 編碼在要求中的 Url。</span><span class="sxs-lookup"><span data-stu-id="1758d-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="1758d-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="1758d-153">FavorUTF8</span></span>|<span data-ttu-id="1758d-154">1</span><span class="sxs-lookup"><span data-stu-id="1758d-154">1</span></span>|<span data-ttu-id="1758d-155">如果不是零，`http.sys`一律要解碼的 URL 為 utf-8 第一次; 如果該轉換會失敗，而且 EnableNonUTF8 為非零的嘗試，Http.sys，然後嘗試將它解碼為 ANSI 或 DBCS。</span><span class="sxs-lookup"><span data-stu-id="1758d-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="1758d-156">如果是零 （和 EnableNonUTF8 為非零）`http.sys`嘗試將它解碼為 ANSI 或 DBCS; 如果不成功，它嘗試 utf-8 轉換。</span><span class="sxs-lookup"><span data-stu-id="1758d-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="1758d-157">當<xref:System.Net.HttpListener>收到要求時，它會使用轉換的 URI，從`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1758d-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="1758d-158">沒有需要支援在 Uri 中的字元和數字以外的字元。</span><span class="sxs-lookup"><span data-stu-id="1758d-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="1758d-159">舉例來說，下列 URI，用來擷取客戶的客戶資訊數字"1/3812 」:</span><span class="sxs-lookup"><span data-stu-id="1758d-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="1758d-160">請注意百分比編碼中的斜線的 Uri (%2f)。</span><span class="sxs-lookup"><span data-stu-id="1758d-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="1758d-161">這是必要的因為在此情況下的斜線字元代表的資料，不是路徑分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1758d-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="1758d-162">將字串傳遞至 Uri 建構函式會導致下列 URI:</span><span class="sxs-lookup"><span data-stu-id="1758d-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="1758d-163">將路徑分割成其區段，會導致下列項目：</span><span class="sxs-lookup"><span data-stu-id="1758d-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="1758d-164">這不是要求的寄件者的意圖。</span><span class="sxs-lookup"><span data-stu-id="1758d-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="1758d-165">如果**unescapeRequestUrl**屬性設為**false**，然後當<xref:System.Net.HttpListener>收到要求時，它會使用原始 URI，而不是從轉換的 URI`http.sys`做為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1758d-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="1758d-166">預設值**unescapeRequestUrl**屬性是 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="1758d-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="1758d-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>屬性可用來取得目前的值**unescapeRequestUrl**適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="1758d-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1758d-168">範例</span><span class="sxs-lookup"><span data-stu-id="1758d-168">Example</span></span>  
 <span data-ttu-id="1758d-169">下列範例示範如何設定<xref:System.Net.HttpListener>類別，在它收到要求時使用的原始 URI，而不是從轉換的 URI`http.sys`來作為輸入<xref:System.Net.HttpListenerRequest.Url%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="1758d-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="1758d-170">項目資訊</span><span class="sxs-lookup"><span data-stu-id="1758d-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="1758d-171">命名空間</span><span class="sxs-lookup"><span data-stu-id="1758d-171">Namespace</span></span>|<span data-ttu-id="1758d-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="1758d-172">System.Net</span></span>|  
|<span data-ttu-id="1758d-173">結構描述名稱</span><span class="sxs-lookup"><span data-stu-id="1758d-173">Schema Name</span></span>||  
|<span data-ttu-id="1758d-174">驗證檔</span><span class="sxs-lookup"><span data-stu-id="1758d-174">Validation File</span></span>||  
|<span data-ttu-id="1758d-175">可以是空白</span><span class="sxs-lookup"><span data-stu-id="1758d-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="1758d-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1758d-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="1758d-177">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1758d-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
