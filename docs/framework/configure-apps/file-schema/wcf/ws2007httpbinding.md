---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 379552f461a79415e3140a8084901e0c1d6b2c32
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140486"
---
# <a name="ws2007httpbinding"></a><span data-ttu-id="18f45-101">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="18f45-101">\<ws2007HttpBinding></span></span>
<span data-ttu-id="18f45-102">定義可互通的繫結，此繫結支援正確版本的 <xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession> 和 <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> 繫結項目。</span><span class="sxs-lookup"><span data-stu-id="18f45-102">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
<span data-ttu-id="18f45-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="18f45-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="18f45-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="18f45-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="18f45-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="18f45-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="18f45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007HttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="18f45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f45-107">語法</span><span class="sxs-lookup"><span data-stu-id="18f45-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
        <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"
                 negotiateServiceCredential="Boolean"
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
                 establishSecurityContext="Boolean"
                 negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18f45-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18f45-108">Attributes and Elements</span></span>  
 <span data-ttu-id="18f45-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18f45-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18f45-110">屬性</span><span class="sxs-lookup"><span data-stu-id="18f45-110">Attributes</span></span>  
  
|<span data-ttu-id="18f45-111">屬性</span><span class="sxs-lookup"><span data-stu-id="18f45-111">Attribute</span></span>|<span data-ttu-id="18f45-112">描述</span><span class="sxs-lookup"><span data-stu-id="18f45-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="18f45-113">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="18f45-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="18f45-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="18f45-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="18f45-115">當您與使用 Cookie 的 ASP.NET Web 服務 (ASMX) 互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="18f45-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="18f45-116">這可確保伺服器傳回的 Cookie 一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="18f45-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="18f45-117">一個指出本機位址是否略過 Proxy 伺服器的值。</span><span class="sxs-lookup"><span data-stu-id="18f45-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="18f45-118">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="18f45-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="18f45-119"><xref:System.TimeSpan> 值，指定用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18f45-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="18f45-120">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="18f45-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="18f45-121">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="18f45-121">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="18f45-122">指定用於剖析統一資源識別元 (URI) 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="18f45-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="18f45-123">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="18f45-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="18f45-124">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="18f45-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="18f45-125">此繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="18f45-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="18f45-126">預設為 524,288 個位元組 (512 × 1,024)。</span><span class="sxs-lookup"><span data-stu-id="18f45-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="18f45-127">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="18f45-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="18f45-128">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，而且緩衝區的記憶體回收也是高度耗費資源的作業。</span><span class="sxs-lookup"><span data-stu-id="18f45-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="18f45-129">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="18f45-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="18f45-130">這可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="18f45-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="18f45-131">使用此繫結所設定之通道可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="18f45-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="18f45-132">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="18f45-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="18f45-133">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="18f45-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="18f45-134">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="18f45-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="18f45-135">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="18f45-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="18f45-136">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="18f45-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18f45-137">-   `Text`：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="18f45-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="18f45-138">-   `Mtom`：使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="18f45-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="18f45-139">預設為 `Text`。</span><span class="sxs-lookup"><span data-stu-id="18f45-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="18f45-140">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="18f45-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="18f45-141">繫結的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="18f45-141">The configuration name of the binding.</span></span> <span data-ttu-id="18f45-142">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="18f45-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="18f45-143">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="18f45-143">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="18f45-144">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="18f45-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="18f45-145"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18f45-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="18f45-146">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="18f45-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="18f45-147">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="18f45-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="18f45-148">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="18f45-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="18f45-149">如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="18f45-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="18f45-150">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="18f45-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="18f45-151"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18f45-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="18f45-152">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="18f45-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="18f45-153">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="18f45-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="18f45-154"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="18f45-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="18f45-155">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="18f45-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="18f45-156">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="18f45-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="18f45-157">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="18f45-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="18f45-158">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="18f45-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18f45-159">-   `UnicodeFffeTextEncoding`： Unicode Big Endian 編碼。</span><span class="sxs-lookup"><span data-stu-id="18f45-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="18f45-160">-   `Utf16TextEncoding`：16位編碼方式。</span><span class="sxs-lookup"><span data-stu-id="18f45-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="18f45-161">-   `Utf8TextEncoding`：8位編碼。</span><span class="sxs-lookup"><span data-stu-id="18f45-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="18f45-162">預設為 `Utf8TextEncoding`。</span><span class="sxs-lookup"><span data-stu-id="18f45-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="18f45-163">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="18f45-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="18f45-164">指定繫結程序是否支援流動 WS-Transactions 的值。</span><span class="sxs-lookup"><span data-stu-id="18f45-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="18f45-165">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="18f45-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="18f45-166">指定是否使用系統自動設定之 HTTP Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="18f45-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="18f45-167">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="18f45-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18f45-168">子項目</span><span class="sxs-lookup"><span data-stu-id="18f45-168">Child Elements</span></span>  
  
|<span data-ttu-id="18f45-169">項目</span><span class="sxs-lookup"><span data-stu-id="18f45-169">Element</span></span>|<span data-ttu-id="18f45-170">描述</span><span class="sxs-lookup"><span data-stu-id="18f45-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18f45-171">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="18f45-171">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="18f45-172">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="18f45-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="18f45-173">此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="18f45-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="18f45-174">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="18f45-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="18f45-175">定義 SOAP 訊息複雜性的條件約束，而這些條件約束可由使用此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="18f45-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="18f45-176">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="18f45-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="18f45-177">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="18f45-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="18f45-178">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="18f45-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18f45-179">父項目</span><span class="sxs-lookup"><span data-stu-id="18f45-179">Parent Elements</span></span>  
  
|<span data-ttu-id="18f45-180">項目</span><span class="sxs-lookup"><span data-stu-id="18f45-180">Element</span></span>|<span data-ttu-id="18f45-181">描述</span><span class="sxs-lookup"><span data-stu-id="18f45-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18f45-182">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="18f45-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="18f45-183">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="18f45-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18f45-184">備註</span><span class="sxs-lookup"><span data-stu-id="18f45-184">Remarks</span></span>  
 <span data-ttu-id="18f45-185">`WS2007HttpBinding` 會加入類似 `WSHttpBinding` 的系統提供繫結，但是會使用 ReliableSession、Security 和 TransactionFlow 通訊協定的先進結構化資訊標準組織 (OASIS) 標準版本。</span><span class="sxs-lookup"><span data-stu-id="18f45-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="18f45-186">使用這個繫結時，不需要變更物件模型或是預設設定。</span><span class="sxs-lookup"><span data-stu-id="18f45-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18f45-187">範例</span><span class="sxs-lookup"><span data-stu-id="18f45-187">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007HttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </ws2007HttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="18f45-188">請參閱</span><span class="sxs-lookup"><span data-stu-id="18f45-188">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="18f45-189">繫結</span><span class="sxs-lookup"><span data-stu-id="18f45-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="18f45-190">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="18f45-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="18f45-191">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="18f45-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="18f45-192">\<binding ></span><span class="sxs-lookup"><span data-stu-id="18f45-192">\<binding></span></span>](bindings.md)
