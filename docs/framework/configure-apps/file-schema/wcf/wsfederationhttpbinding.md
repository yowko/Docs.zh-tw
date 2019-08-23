---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 3c4edc17fd669fbe23ec38ff26a61e867c04c561
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915073"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="c0608-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0608-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="c0608-102">定義支援 WS-Federation 的繫結。</span><span class="sxs-lookup"><span data-stu-id="c0608-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="c0608-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0608-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="c0608-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c0608-104">\<bindings></span></span>\
<span data-ttu-id="c0608-105">wsFederationBinding 項目</span><span class="sxs-lookup"><span data-stu-id="c0608-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="c0608-106">語法</span><span class="sxs-lookup"><span data-stu-id="c0608-106">Syntax</span></span>

```xml
<wsFederationHttpBinding>
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
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
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
</wsFederationBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0608-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0608-107">Attributes and Elements</span></span>

<span data-ttu-id="c0608-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0608-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0608-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c0608-109">Attributes</span></span>

|<span data-ttu-id="c0608-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0608-110">Attribute</span></span>|<span data-ttu-id="c0608-111">說明</span><span class="sxs-lookup"><span data-stu-id="c0608-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c0608-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="c0608-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="c0608-113">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c0608-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="c0608-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c0608-114">The default is `false`.</span></span>|
|<span data-ttu-id="c0608-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="c0608-115">closeTimeout</span></span>|<span data-ttu-id="c0608-116"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c0608-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="c0608-117">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="c0608-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0608-118">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="c0608-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0608-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="c0608-119">hostnameComparisonMode</span></span>|<span data-ttu-id="c0608-120">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="c0608-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="c0608-121">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="c0608-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="c0608-122">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="c0608-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="c0608-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c0608-123">maxBufferPoolSize</span></span>|<span data-ttu-id="c0608-124">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="c0608-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="c0608-125">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="c0608-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="c0608-126">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c0608-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="c0608-127">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="c0608-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="c0608-128">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="c0608-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="c0608-129">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="c0608-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="c0608-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c0608-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="c0608-131">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="c0608-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="c0608-132">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0608-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="c0608-133">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="c0608-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="c0608-134">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="c0608-134">The default is 65536.</span></span>|
|<span data-ttu-id="c0608-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="c0608-135">messageEncoding</span></span>|<span data-ttu-id="c0608-136">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="c0608-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="c0608-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c0608-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c0608-138">文字使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="c0608-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="c0608-139">Mtom使用訊息傳輸組織機制 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="c0608-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="c0608-140">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="c0608-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="c0608-141">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="c0608-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="c0608-142">NAME</span><span class="sxs-lookup"><span data-stu-id="c0608-142">name</span></span>|<span data-ttu-id="c0608-143">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="c0608-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="c0608-144">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="c0608-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="c0608-145">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="c0608-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c0608-146">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="c0608-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="c0608-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="c0608-147">openTimeout</span></span>|<span data-ttu-id="c0608-148"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c0608-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="c0608-149">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="c0608-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0608-150">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="c0608-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0608-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="c0608-151">privacyNoticeAt</span></span>|<span data-ttu-id="c0608-152">字串，指定隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="c0608-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="c0608-153">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="c0608-153">privacyNoticeVersion</span></span>|<span data-ttu-id="c0608-154">指定目前隱私權注意事項之版本的整數。</span><span class="sxs-lookup"><span data-stu-id="c0608-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="c0608-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="c0608-155">proxyAddress</span></span>|<span data-ttu-id="c0608-156">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="c0608-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="c0608-157">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="c0608-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="c0608-158">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="c0608-158">The default is `null`.</span></span>|
|<span data-ttu-id="c0608-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="c0608-159">receiveTimeout</span></span>|<span data-ttu-id="c0608-160"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c0608-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="c0608-161">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="c0608-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0608-162">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="c0608-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="c0608-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="c0608-163">sendTimeout</span></span>|<span data-ttu-id="c0608-164"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="c0608-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="c0608-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="c0608-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="c0608-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="c0608-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="c0608-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="c0608-167">textEncoding</span></span>|<span data-ttu-id="c0608-168">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c0608-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="c0608-169">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="c0608-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c0608-170">BigEndianUnicodeUnicode BigEndian 編碼。</span><span class="sxs-lookup"><span data-stu-id="c0608-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="c0608-171">消除16位編碼。</span><span class="sxs-lookup"><span data-stu-id="c0608-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="c0608-172">UTF88位編碼</span><span class="sxs-lookup"><span data-stu-id="c0608-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="c0608-173">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="c0608-173">The default is UTF8.</span></span> <span data-ttu-id="c0608-174">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="c0608-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="c0608-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="c0608-175">transactionFlow</span></span>|<span data-ttu-id="c0608-176">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="c0608-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="c0608-177">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c0608-177">The default is `false`.</span></span>|
|<span data-ttu-id="c0608-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="c0608-178">useDefaultWebProxy</span></span>|<span data-ttu-id="c0608-179">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="c0608-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="c0608-180">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="c0608-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="c0608-181">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c0608-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c0608-182">子元素</span><span class="sxs-lookup"><span data-stu-id="c0608-182">Child Elements</span></span>

|<span data-ttu-id="c0608-183">項目</span><span class="sxs-lookup"><span data-stu-id="c0608-183">Element</span></span>|<span data-ttu-id="c0608-184">描述</span><span class="sxs-lookup"><span data-stu-id="c0608-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0608-185">\<security></span><span class="sxs-lookup"><span data-stu-id="c0608-185">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="c0608-186">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="c0608-186">Defines the security settings for the message.</span></span> <span data-ttu-id="c0608-187">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="c0608-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="c0608-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c0608-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="c0608-189">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="c0608-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="c0608-190">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="c0608-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="c0608-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c0608-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="c0608-192">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="c0608-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0608-193">父項目</span><span class="sxs-lookup"><span data-stu-id="c0608-193">Parent Elements</span></span>

|<span data-ttu-id="c0608-194">項目</span><span class="sxs-lookup"><span data-stu-id="c0608-194">Element</span></span>|<span data-ttu-id="c0608-195">說明</span><span class="sxs-lookup"><span data-stu-id="c0608-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0608-196">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c0608-196">\<bindings></span></span>](bindings.md)|<span data-ttu-id="c0608-197">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="c0608-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0608-198">備註</span><span class="sxs-lookup"><span data-stu-id="c0608-198">Remarks</span></span>

<span data-ttu-id="c0608-199">聯合是在多個系統上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="c0608-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="c0608-200">這些識別可以指向使用者或電腦。</span><span class="sxs-lookup"><span data-stu-id="c0608-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="c0608-201">聯合 HTTP 支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="c0608-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="c0608-202">此系結會提供 WS-同盟通訊協定的 Windows Communication Foundation (WCF) 支援。</span><span class="sxs-lookup"><span data-stu-id="c0608-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="c0608-203">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="c0608-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="c0608-204">繫結是由繫結項目的堆疊組成。</span><span class="sxs-lookup"><span data-stu-id="c0608-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="c0608-205">位於</span><span class="sxs-lookup"><span data-stu-id="c0608-205">The stack of binding elements in</span></span>

<span data-ttu-id="c0608-206">`wsFederationHttpBinding` 與 `wsHttpBinding` 中包含的項目相同。</span><span class="sxs-lookup"><span data-stu-id="c0608-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="c0608-207">當[ \<安全性 >](security-of-wsfederationhttpbinding.md)設定為<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>的預設值時。</span><span class="sxs-lookup"><span data-stu-id="c0608-207">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="c0608-208">會控制 message [ \<>](message-element-of-wsfederationhttpbinding.md)中訊息安全性設定的詳細資料。 `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="c0608-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="c0608-209">請注意, [ [ \<安全性 >](security-of-wsfederationhttpbinding.md) ] 元素僅提供 [取得存取], 因為一旦建立系結之後, 就無法變更系結所使用的安全性。</span><span class="sxs-lookup"><span data-stu-id="c0608-209">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="c0608-210">`wsFederationHttpBinding`也會提供 privacyNoticeAt 屬性, 以設定和抓取隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="c0608-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="c0608-211">維持原則的安全相當重要，特別是在聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="c0608-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="c0608-212">建議使用某種形式的安全性，例如 HTTPS，來保護原則不受惡意使用者攻擊。</span><span class="sxs-lookup"><span data-stu-id="c0608-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="c0608-213">在使用這個繫結的聯合案例中，服務原則可能有重要的資訊，例如用來加密所發行 (SAML) 權杖的金鑰、放入權杖內的宣告類型等等。</span><span class="sxs-lookup"><span data-stu-id="c0608-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="c0608-214">如果這個原則遭到竄改，攻擊者可能會發現可導致進一步竄改、資訊洩露和其他惡意行為的已發行權杖金鑰。</span><span class="sxs-lookup"><span data-stu-id="c0608-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="c0608-215">為了防止發生這種情況，必須安全地從服務取得原則 (例如，使用 HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="c0608-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="c0608-216">如需此系結的詳細資訊[, 請參閱如何:建立 WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="c0608-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0608-217">範例</span><span class="sxs-lookup"><span data-stu-id="c0608-217">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsFederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="saml"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </wsFederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c0608-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0608-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="c0608-219">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c0608-219">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c0608-220">繫結</span><span class="sxs-lookup"><span data-stu-id="c0608-220">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c0608-221">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c0608-221">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c0608-222">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="c0608-222">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c0608-223">\<binding></span><span class="sxs-lookup"><span data-stu-id="c0608-223">\<binding></span></span>](../../../misc/binding.md)
