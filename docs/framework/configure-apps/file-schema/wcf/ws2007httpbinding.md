---
title: <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 102e220ad01410568a18ce4ea6fac06ca8c15230
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558728"
---
# \<ws2007HttpBinding>
<span data-ttu-id="67443-101">定義可互通的繫結，此繫結支援正確版本的 <xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession> 和 <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> 繫結項目。</span><span class="sxs-lookup"><span data-stu-id="67443-101">Defines an interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007HttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="67443-102">語法</span><span class="sxs-lookup"><span data-stu-id="67443-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67443-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67443-103">Attributes and Elements</span></span>  
 <span data-ttu-id="67443-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67443-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67443-105">屬性</span><span class="sxs-lookup"><span data-stu-id="67443-105">Attributes</span></span>  
  
|<span data-ttu-id="67443-106">屬性</span><span class="sxs-lookup"><span data-stu-id="67443-106">Attribute</span></span>|<span data-ttu-id="67443-107">描述</span><span class="sxs-lookup"><span data-stu-id="67443-107">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="67443-108">表示用戶端是否接受 Cookie 並在未來的要求傳播 Cookie 的值。</span><span class="sxs-lookup"><span data-stu-id="67443-108">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="67443-109">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="67443-109">The default is `false`.</span></span><br /><br /> <span data-ttu-id="67443-110">當您與使用 Cookie 的 ASP.NET Web 服務 (ASMX) 互動時，可以使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="67443-110">You can use this property when you interact with ASP.NET Web services (ASMX) that use cookies.</span></span> <span data-ttu-id="67443-111">這可確保伺服器傳回的 Cookie 一定會自動複製到該服務未來所有的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="67443-111">This ensures that cookies that the server returns are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="67443-112">一個指出本機位址是否略過 Proxy 伺服器的值。</span><span class="sxs-lookup"><span data-stu-id="67443-112">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="67443-113">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="67443-113">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="67443-114"><xref:System.TimeSpan> 值，指定用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="67443-114">A <xref:System.TimeSpan> value that specifies the time interval for a close operation to complete.</span></span> <span data-ttu-id="67443-115">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="67443-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67443-116">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="67443-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="67443-117">指定用於剖析統一資源識別元 (URI) 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="67443-117">Specifies the HTTP hostname comparison mode used to parse Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="67443-118">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="67443-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="67443-119">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="67443-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="67443-120">此繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="67443-120">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="67443-121">預設為 524,288 個位元組 (512 × 1,024)。</span><span class="sxs-lookup"><span data-stu-id="67443-121">The default is 524,288 bytes (512 × 1,024).</span></span> <span data-ttu-id="67443-122">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="67443-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="67443-123">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，而且緩衝區的記憶體回收也是高度耗費資源的作業。</span><span class="sxs-lookup"><span data-stu-id="67443-123">Creating and destroying buffers each time they are used is expensive, as is garbage collection for buffers.</span></span> <span data-ttu-id="67443-124">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="67443-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool when you are done.</span></span> <span data-ttu-id="67443-125">這可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="67443-125">This avoids the overhead in creating and destroying buffers.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="67443-126">使用此繫結所設定之通道可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="67443-126">The maximum message size, in bytes, including headers, which a channel configured with this binding, can receive.</span></span> <span data-ttu-id="67443-127">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="67443-127">The sender of a message exceeding this limit receives a SOAP fault.</span></span> <span data-ttu-id="67443-128">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="67443-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="67443-129">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="67443-129">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="67443-130">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="67443-130">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="67443-131">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="67443-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="67443-132">-   `Text`：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="67443-132">-   `Text`: Use a text message encoder.</span></span><br /><span data-ttu-id="67443-133">-   `Mtom`：使用訊息傳輸組織機制 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="67443-133">-   `Mtom`: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="67443-134">預設為 `Text`。</span><span class="sxs-lookup"><span data-stu-id="67443-134">The default is `Text`.</span></span><br /><br /> <span data-ttu-id="67443-135">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="67443-135">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="67443-136">繫結的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="67443-136">The configuration name of the binding.</span></span> <span data-ttu-id="67443-137">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="67443-137">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="67443-138">從 .NET Framework 4 開始，系結和行為不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="67443-138">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="67443-139">如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="67443-139">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="67443-140"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="67443-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="67443-141">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="67443-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67443-142">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="67443-142">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="67443-143">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="67443-143">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="67443-144">如果 `useSystemWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="67443-144">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="67443-145">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="67443-145">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="67443-146"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="67443-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="67443-147">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="67443-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67443-148">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="67443-148">The default is 00:01:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="67443-149"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="67443-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="67443-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="67443-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="67443-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="67443-151">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="67443-152">指定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="67443-152">Specifies the character set encoding to use for emitting messages on the binding.</span></span> <span data-ttu-id="67443-153">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="67443-153">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="67443-154">-   `UnicodeFffeTextEncoding`： Unicode Big Endian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="67443-154">-   `UnicodeFffeTextEncoding`: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="67443-155">-   `Utf16TextEncoding`：16位編碼。</span><span class="sxs-lookup"><span data-stu-id="67443-155">-   `Utf16TextEncoding`: 16-bit encoding.</span></span><br /><span data-ttu-id="67443-156">-   `Utf8TextEncoding`：8位編碼。</span><span class="sxs-lookup"><span data-stu-id="67443-156">-   `Utf8TextEncoding`: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="67443-157">預設為 `Utf8TextEncoding`。</span><span class="sxs-lookup"><span data-stu-id="67443-157">The default is `Utf8TextEncoding`.</span></span><br /><br /> <span data-ttu-id="67443-158">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="67443-158">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="67443-159">指定繫結程序是否支援流動 WS-Transactions 的值。</span><span class="sxs-lookup"><span data-stu-id="67443-159">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="67443-160">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="67443-160">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="67443-161">指定是否使用系統自動設定之 HTTP Proxy 的值。</span><span class="sxs-lookup"><span data-stu-id="67443-161">A value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="67443-162">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="67443-162">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67443-163">子元素</span><span class="sxs-lookup"><span data-stu-id="67443-163">Child Elements</span></span>  
  
|<span data-ttu-id="67443-164">項目</span><span class="sxs-lookup"><span data-stu-id="67443-164">Element</span></span>|<span data-ttu-id="67443-165">描述</span><span class="sxs-lookup"><span data-stu-id="67443-165">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="67443-166">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="67443-166">Defines the security settings for the binding.</span></span> <span data-ttu-id="67443-167">此項目的型別為 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="67443-167">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="67443-168">定義 SOAP 訊息複雜性的條件約束，而這些條件約束可由使用此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="67443-168">Defines the constraints on the complexity of SOAP messages that endpoints configured with this binding can process.</span></span> <span data-ttu-id="67443-169">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="67443-169">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="67443-170">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="67443-170">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67443-171">父項目</span><span class="sxs-lookup"><span data-stu-id="67443-171">Parent Elements</span></span>  
  
|<span data-ttu-id="67443-172">項目</span><span class="sxs-lookup"><span data-stu-id="67443-172">Element</span></span>|<span data-ttu-id="67443-173">描述</span><span class="sxs-lookup"><span data-stu-id="67443-173">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="67443-174">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="67443-174">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67443-175">備註</span><span class="sxs-lookup"><span data-stu-id="67443-175">Remarks</span></span>  
 <span data-ttu-id="67443-176">`WS2007HttpBinding` 會加入類似 `WSHttpBinding` 的系統提供繫結，但是會使用 ReliableSession、Security 和 TransactionFlow 通訊協定的先進結構化資訊標準組織 (OASIS) 標準版本。</span><span class="sxs-lookup"><span data-stu-id="67443-176">The `WS2007HttpBinding` adds a system-provided binding similar to `WSHttpBinding` but uses the Organization for the Advancement of Structured Information Standards (OASIS) standard versions of the ReliableSession, Security, and TransactionFlow protocols.</span></span> <span data-ttu-id="67443-177">使用這個繫結時，不需要變更物件模型或是預設設定。</span><span class="sxs-lookup"><span data-stu-id="67443-177">No changes to the object model or default settings are required when using this binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67443-178">範例</span><span class="sxs-lookup"><span data-stu-id="67443-178">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67443-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67443-179">See also</span></span>

- <xref:System.ServiceModel.WS2007HttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>
- [<span data-ttu-id="67443-180">繫結</span><span class="sxs-lookup"><span data-stu-id="67443-180">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="67443-181">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="67443-181">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="67443-182">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="67443-182">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
