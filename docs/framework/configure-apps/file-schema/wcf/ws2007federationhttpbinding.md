---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: fe9ab2e19706a5d295b5916aeb818621d1132c11
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558767"
---
# \<ws2007FederationHttpBinding>

<span data-ttu-id="9770f-101">衍生自 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 並支援聯合安全性的安全且互通的系結。</span><span class="sxs-lookup"><span data-stu-id="9770f-101">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="9770f-102">語法</span><span class="sxs-lookup"><span data-stu-id="9770f-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9770f-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9770f-103">Attributes and Elements</span></span>

<span data-ttu-id="9770f-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9770f-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9770f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="9770f-105">Attributes</span></span>

|<span data-ttu-id="9770f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9770f-106">Attribute</span></span>|<span data-ttu-id="9770f-107">描述</span><span class="sxs-lookup"><span data-stu-id="9770f-107">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="9770f-108">一個指出本機位址是否略過 Proxy 伺服器的值。</span><span class="sxs-lookup"><span data-stu-id="9770f-108">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9770f-109">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9770f-109">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="9770f-110"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9770f-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9770f-111">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9770f-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9770f-112">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9770f-112">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="9770f-113">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="9770f-113">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9770f-114">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="9770f-114">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9770f-115">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="9770f-115">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="9770f-116">此繫結的緩衝集區大小上限。</span><span class="sxs-lookup"><span data-stu-id="9770f-116">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9770f-117">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="9770f-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9770f-118">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9770f-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9770f-119">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="9770f-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9770f-120">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="9770f-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9770f-121">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="9770f-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="9770f-122">在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="9770f-122">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9770f-123">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9770f-123">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="9770f-124">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="9770f-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9770f-125">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="9770f-125">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="9770f-126">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="9770f-126">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="9770f-127">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="9770f-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9770f-128">-Text：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="9770f-128">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9770f-129">-Mtom：使用訊息傳輸組織機制 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="9770f-129">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9770f-130">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="9770f-130">The default is Text.</span></span><br /><br /> <span data-ttu-id="9770f-131">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="9770f-131">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="9770f-132">繫結的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="9770f-132">The configuration name of the binding.</span></span> <span data-ttu-id="9770f-133">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="9770f-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9770f-134">從 .NET Framework 4 開始，系結和行為不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="9770f-134">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9770f-135">如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="9770f-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="9770f-136"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9770f-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9770f-137">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9770f-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9770f-138">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9770f-138">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="9770f-139">隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="9770f-139">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="9770f-140">目前隱私權注意事項的版本。</span><span class="sxs-lookup"><span data-stu-id="9770f-140">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="9770f-141">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="9770f-141">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="9770f-142">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9770f-142">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="9770f-143">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9770f-143">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="9770f-144"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9770f-144">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9770f-145">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9770f-145">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9770f-146">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="9770f-146">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="9770f-147"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9770f-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9770f-148">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9770f-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9770f-149">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9770f-149">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="9770f-150">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9770f-150">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9770f-151">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="9770f-151">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9770f-152">-BigEndianUnicode： Unicode Big Endian 編碼。</span><span class="sxs-lookup"><span data-stu-id="9770f-152">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="9770f-153">-Unicode：16位編碼。</span><span class="sxs-lookup"><span data-stu-id="9770f-153">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9770f-154">-UTF8：8位編碼。</span><span class="sxs-lookup"><span data-stu-id="9770f-154">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="9770f-155">預設值為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="9770f-155">The default is UTF8.</span></span> <span data-ttu-id="9770f-156">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="9770f-156">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="9770f-157">指定繫結程序是否支援流動 WS-Transactions 的值。</span><span class="sxs-lookup"><span data-stu-id="9770f-157">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9770f-158">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9770f-158">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="9770f-159">一個值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="9770f-159">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="9770f-160">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="9770f-160">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="9770f-161">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9770f-161">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9770f-162">子元素</span><span class="sxs-lookup"><span data-stu-id="9770f-162">Child Elements</span></span>

|<span data-ttu-id="9770f-163">項目</span><span class="sxs-lookup"><span data-stu-id="9770f-163">Element</span></span>|<span data-ttu-id="9770f-164">描述</span><span class="sxs-lookup"><span data-stu-id="9770f-164">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="9770f-165">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9770f-165">Defines the security settings for the message.</span></span> <span data-ttu-id="9770f-166">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="9770f-166">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="9770f-167">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="9770f-167">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9770f-168">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="9770f-168">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|[\<reliableSession>](/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="9770f-169">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9770f-169">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9770f-170">父項目</span><span class="sxs-lookup"><span data-stu-id="9770f-170">Parent Elements</span></span>

|<span data-ttu-id="9770f-171">項目</span><span class="sxs-lookup"><span data-stu-id="9770f-171">Element</span></span>|<span data-ttu-id="9770f-172">描述</span><span class="sxs-lookup"><span data-stu-id="9770f-172">Description</span></span>|
|-------------|-----------------|
|[\<bindings>](bindings.md)|<span data-ttu-id="9770f-173">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="9770f-173">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9770f-174">備註</span><span class="sxs-lookup"><span data-stu-id="9770f-174">Remarks</span></span>

<span data-ttu-id="9770f-175">聯合是在多個企業或信任網域上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="9770f-175">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="9770f-176">它使用 WS-Trust 通訊協定從一信任網域對應身分識別表示至其他信任網域。</span><span class="sxs-lookup"><span data-stu-id="9770f-176">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="9770f-177">聯合 HTTP 繫結支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="9770f-177">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="9770f-178">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="9770f-178">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="9770f-179">如需詳細資訊，請參閱 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="9770f-179">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="9770f-180">範例</span><span class="sxs-lookup"><span data-stu-id="9770f-180">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9770f-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9770f-181">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [\<wsFederationHttpBinding>](wsfederationhttpbinding.md)
- [<span data-ttu-id="9770f-182">繫結</span><span class="sxs-lookup"><span data-stu-id="9770f-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9770f-183">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9770f-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9770f-184">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="9770f-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
