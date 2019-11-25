---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 20ba643fddbac8a488e5457f0195cc253d4d23f7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139321"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="41805-101">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="41805-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="41805-102">一種安全且互通的系結，衍生自[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)並支援聯合安全性。</span><span class="sxs-lookup"><span data-stu-id="41805-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

<span data-ttu-id="41805-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="41805-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="41805-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="41805-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="41805-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="41805-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="41805-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007FederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="41805-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41805-107">語法</span><span class="sxs-lookup"><span data-stu-id="41805-107">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="41805-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="41805-108">Attributes and Elements</span></span>

<span data-ttu-id="41805-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="41805-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="41805-110">屬性</span><span class="sxs-lookup"><span data-stu-id="41805-110">Attributes</span></span>

|<span data-ttu-id="41805-111">屬性</span><span class="sxs-lookup"><span data-stu-id="41805-111">Attribute</span></span>|<span data-ttu-id="41805-112">描述</span><span class="sxs-lookup"><span data-stu-id="41805-112">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="41805-113">一個指出本機位址是否略過 Proxy 伺服器的值。</span><span class="sxs-lookup"><span data-stu-id="41805-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="41805-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="41805-114">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="41805-115"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="41805-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="41805-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="41805-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41805-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="41805-117">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="41805-118">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="41805-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="41805-119">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="41805-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="41805-120">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="41805-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="41805-121">此繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="41805-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="41805-122">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="41805-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="41805-123">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="41805-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="41805-124">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="41805-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="41805-125">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="41805-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="41805-126">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="41805-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="41805-127">在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="41805-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="41805-128">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="41805-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="41805-129">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="41805-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="41805-130">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="41805-130">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="41805-131">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="41805-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="41805-132">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="41805-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41805-133">-Text：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="41805-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="41805-134">-Mtom：使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="41805-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="41805-135">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="41805-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="41805-136">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="41805-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="41805-137">繫結的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="41805-137">The configuration name of the binding.</span></span> <span data-ttu-id="41805-138">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="41805-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="41805-139">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="41805-139">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="41805-140">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="41805-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="41805-141"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="41805-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="41805-142">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="41805-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41805-143">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="41805-143">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="41805-144">隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="41805-144">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="41805-145">目前隱私權注意事項的版本。</span><span class="sxs-lookup"><span data-stu-id="41805-145">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="41805-146">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="41805-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="41805-147">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="41805-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="41805-148">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="41805-148">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="41805-149"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="41805-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="41805-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="41805-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41805-151">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="41805-151">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="41805-152"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="41805-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="41805-153">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="41805-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="41805-154">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="41805-154">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="41805-155">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="41805-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="41805-156">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="41805-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="41805-157">-BigEndianUnicode： Unicode Big Endian 編碼。</span><span class="sxs-lookup"><span data-stu-id="41805-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="41805-158">-Unicode：16位編碼方式。</span><span class="sxs-lookup"><span data-stu-id="41805-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="41805-159">-UTF8：8位編碼。</span><span class="sxs-lookup"><span data-stu-id="41805-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="41805-160">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="41805-160">The default is UTF8.</span></span> <span data-ttu-id="41805-161">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="41805-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="41805-162">指定繫結程序是否支援流動 WS-Transactions 的值。</span><span class="sxs-lookup"><span data-stu-id="41805-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="41805-163">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="41805-163">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="41805-164">一個值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="41805-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="41805-165">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="41805-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="41805-166">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="41805-166">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="41805-167">子項目</span><span class="sxs-lookup"><span data-stu-id="41805-167">Child Elements</span></span>

|<span data-ttu-id="41805-168">項目</span><span class="sxs-lookup"><span data-stu-id="41805-168">Element</span></span>|<span data-ttu-id="41805-169">描述</span><span class="sxs-lookup"><span data-stu-id="41805-169">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41805-170">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="41805-170">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="41805-171">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="41805-171">Defines the security settings for the message.</span></span> <span data-ttu-id="41805-172">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="41805-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="41805-173">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="41805-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="41805-174">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="41805-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="41805-175">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="41805-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="41805-176">[\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41805-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="41805-177">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="41805-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="41805-178">父項目</span><span class="sxs-lookup"><span data-stu-id="41805-178">Parent Elements</span></span>

|<span data-ttu-id="41805-179">項目</span><span class="sxs-lookup"><span data-stu-id="41805-179">Element</span></span>|<span data-ttu-id="41805-180">描述</span><span class="sxs-lookup"><span data-stu-id="41805-180">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41805-181">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="41805-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="41805-182">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="41805-182">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="41805-183">備註</span><span class="sxs-lookup"><span data-stu-id="41805-183">Remarks</span></span>

<span data-ttu-id="41805-184">聯合是在多個企業或信任網域上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="41805-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="41805-185">它使用 WS-Trust 通訊協定從一信任網域對應身分識別表示至其他信任網域。</span><span class="sxs-lookup"><span data-stu-id="41805-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="41805-186">聯合 HTTP 繫結支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="41805-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="41805-187">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="41805-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="41805-188">如需詳細資訊，請參閱[\<wsFederationHttpBinding >](wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="41805-188">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="41805-189">範例</span><span class="sxs-lookup"><span data-stu-id="41805-189">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="41805-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="41805-190">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="41805-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="41805-191">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="41805-192">繫結</span><span class="sxs-lookup"><span data-stu-id="41805-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="41805-193">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="41805-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="41805-194">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="41805-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="41805-195">\<binding ></span><span class="sxs-lookup"><span data-stu-id="41805-195">\<binding></span></span>](bindings.md)
