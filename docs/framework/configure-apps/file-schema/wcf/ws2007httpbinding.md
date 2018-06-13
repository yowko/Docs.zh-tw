---
title: '&lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 6531e35cbed56029a8f772f0cd63aad521a166ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759084"
---
# <a name="ltws2007httpbindinggt"></a><span data-ttu-id="b8e86-102">&lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b8e86-102">&lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="b8e86-103">定義可互通的繫結，此繫結支援正確版本的 <xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession> 和 <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> 繫結項目。</span><span class="sxs-lookup"><span data-stu-id="b8e86-103">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
 <span data-ttu-id="b8e86-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b8e86-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b8e86-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b8e86-105">\<bindings></span></span>  
<span data-ttu-id="b8e86-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="b8e86-106">\<ws2007HttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e86-107">語法</span><span class="sxs-lookup"><span data-stu-id="b8e86-107">Syntax</span></span>  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
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
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e86-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8e86-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e86-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8e86-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e86-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e86-110">Attributes</span></span>  
  
|<span data-ttu-id="b8e86-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b8e86-111">Attribute</span></span>|<span data-ttu-id="b8e86-112">描述</span><span class="sxs-lookup"><span data-stu-id="b8e86-112">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="b8e86-113">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="b8e86-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="b8e86-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-114">The default is `false`.</span></span><br /><br /> <span data-ttu-id="b8e86-115">當您與使用 Cookie 的 ASP.NET Web 服務 (ASMX) 互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b8e86-115">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="b8e86-116">這可確保伺服器傳回的 Cookie 一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="b8e86-116">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="b8e86-117">一個指出本機位址是否略過 Proxy 伺服器的值。</span><span class="sxs-lookup"><span data-stu-id="b8e86-117">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="b8e86-118">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-118">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="b8e86-119"><xref:System.TimeSpan> 值，指定用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b8e86-119">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="b8e86-120">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8e86-121">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="b8e86-121">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="b8e86-122">指定用於剖析統一資源識別元 (URI) 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="b8e86-122">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="b8e86-123">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="b8e86-123">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b8e86-124">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="b8e86-124">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b8e86-125">此繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="b8e86-125">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b8e86-126">預設為 524,288 個位元組 (512 × 1,024)。</span><span class="sxs-lookup"><span data-stu-id="b8e86-126">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="b8e86-127">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b8e86-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b8e86-128">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，而且緩衝區的記憶體回收也是高度耗費資源的作業。</span><span class="sxs-lookup"><span data-stu-id="b8e86-128">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="b8e86-129">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="b8e86-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="b8e86-130">這可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="b8e86-130">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b8e86-131">使用此繫結所設定之通道可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="b8e86-131">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="b8e86-132">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8e86-132">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="b8e86-133">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="b8e86-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b8e86-134">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="b8e86-134">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="b8e86-135">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="b8e86-135">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="b8e86-136">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="b8e86-136">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b8e86-137">-   `Text`： 使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="b8e86-137">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="b8e86-138">-   `Mtom`： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="b8e86-138">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="b8e86-139">預設值為 `Text`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-139">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="b8e86-140">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-140">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="b8e86-141">繫結的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="b8e86-141">The configuration name of the binding.</span></span> <span data-ttu-id="b8e86-142">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="b8e86-142">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b8e86-143">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="b8e86-143">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b8e86-144">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b8e86-144">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b8e86-145"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b8e86-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b8e86-146">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8e86-147">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="b8e86-147">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="b8e86-148">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="b8e86-148">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="b8e86-149">如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-149">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="b8e86-150">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-150">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b8e86-151"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b8e86-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b8e86-152">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8e86-153">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="b8e86-153">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b8e86-154"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="b8e86-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b8e86-155">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8e86-156">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="b8e86-156">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b8e86-157">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b8e86-157">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="b8e86-158">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="b8e86-158">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b8e86-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b8e86-159">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="b8e86-160">-   `Utf16TextEncoding`: 16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b8e86-160">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="b8e86-161">-   `Utf8TextEncoding`: 8 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="b8e86-161">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="b8e86-162">預設值為 `Utf8TextEncoding`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-162">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="b8e86-163">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-163">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="b8e86-164">指定繫結是否支援流動 WS-Transactions 的值。</span><span class="sxs-lookup"><span data-stu-id="b8e86-164">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b8e86-165">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-165">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="b8e86-166">指定是否使用系統自動設定之 HTTP Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="b8e86-166">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="b8e86-167">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b8e86-167">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8e86-168">子項目</span><span class="sxs-lookup"><span data-stu-id="b8e86-168">Child Elements</span></span>  
  
|<span data-ttu-id="b8e86-169">項目</span><span class="sxs-lookup"><span data-stu-id="b8e86-169">Element</span></span>|<span data-ttu-id="b8e86-170">描述</span><span class="sxs-lookup"><span data-stu-id="b8e86-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e86-171">\<security></span><span class="sxs-lookup"><span data-stu-id="b8e86-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="b8e86-172">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="b8e86-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="b8e86-173">此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-173">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="b8e86-174">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b8e86-174">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="b8e86-175">定義 SOAP 訊息複雜性的條件約束，而這些條件約束可由使用此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="b8e86-175">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="b8e86-176">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="b8e86-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="b8e86-177">reliableSession</span><span class="sxs-lookup"><span data-stu-id="b8e86-177">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="b8e86-178">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="b8e86-178">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e86-179">父項目</span><span class="sxs-lookup"><span data-stu-id="b8e86-179">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e86-180">項目</span><span class="sxs-lookup"><span data-stu-id="b8e86-180">Element</span></span>|<span data-ttu-id="b8e86-181">描述</span><span class="sxs-lookup"><span data-stu-id="b8e86-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e86-182">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b8e86-182">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b8e86-183">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="b8e86-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e86-184">備註</span><span class="sxs-lookup"><span data-stu-id="b8e86-184">Remarks</span></span>  
 <span data-ttu-id="b8e86-185">`WS2007HttpBinding` 會加入類似 `WSHttpBinding` 的系統提供繫結，但是會使用 ReliableSession、Security 和 TransactionFlow 通訊協定的先進結構化資訊標準組織 (OASIS) 標準版本。</span><span class="sxs-lookup"><span data-stu-id="b8e86-185">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="b8e86-186">使用這個繫結時，不需要變更物件模型或是預設設定。</span><span class="sxs-lookup"><span data-stu-id="b8e86-186">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e86-187">範例</span><span class="sxs-lookup"><span data-stu-id="b8e86-187">Example</span></span>  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
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
  
## <a name="see-also"></a><span data-ttu-id="b8e86-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8e86-188">See Also</span></span>  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [<span data-ttu-id="b8e86-189">繫結</span><span class="sxs-lookup"><span data-stu-id="b8e86-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b8e86-190">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b8e86-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b8e86-191">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="b8e86-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b8e86-192">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b8e86-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
