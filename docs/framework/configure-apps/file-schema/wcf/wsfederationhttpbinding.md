---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: a605d3241ec62f5648e3439b327153f3fb4590df
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399026"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="9017f-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9017f-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="9017f-102">定義支援 WS-Federation 的繫結。</span><span class="sxs-lookup"><span data-stu-id="9017f-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="9017f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9017f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9017f-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9017f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9017f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9017f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9017f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsFederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="9017f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsFederationHttpBinding>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="9017f-107">語法</span><span class="sxs-lookup"><span data-stu-id="9017f-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="9017f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9017f-108">Attributes and Elements</span></span>

<span data-ttu-id="9017f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9017f-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9017f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9017f-110">Attributes</span></span>

|<span data-ttu-id="9017f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9017f-111">Attribute</span></span>|<span data-ttu-id="9017f-112">說明</span><span class="sxs-lookup"><span data-stu-id="9017f-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="9017f-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="9017f-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="9017f-114">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9017f-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="9017f-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9017f-115">The default is `false`.</span></span>|
|<span data-ttu-id="9017f-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="9017f-116">closeTimeout</span></span>|<span data-ttu-id="9017f-117"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9017f-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9017f-118">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9017f-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9017f-119">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9017f-119">The default is 00:01:00.</span></span>|
|<span data-ttu-id="9017f-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="9017f-120">hostnameComparisonMode</span></span>|<span data-ttu-id="9017f-121">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="9017f-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="9017f-122">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="9017f-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="9017f-123">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="9017f-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="9017f-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9017f-124">maxBufferPoolSize</span></span>|<span data-ttu-id="9017f-125">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="9017f-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="9017f-126">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="9017f-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="9017f-127">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9017f-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="9017f-128">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="9017f-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9017f-129">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="9017f-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9017f-130">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="9017f-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="9017f-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9017f-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="9017f-132">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="9017f-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="9017f-133">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9017f-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="9017f-134">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="9017f-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9017f-135">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="9017f-135">The default is 65536.</span></span>|
|<span data-ttu-id="9017f-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="9017f-136">messageEncoding</span></span>|<span data-ttu-id="9017f-137">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="9017f-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="9017f-138">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="9017f-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9017f-139">文字使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="9017f-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="9017f-140">Mtom使用訊息傳輸組織機制1.0 （MTOM）編碼器。</span><span class="sxs-lookup"><span data-stu-id="9017f-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="9017f-141">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="9017f-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="9017f-142">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="9017f-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="9017f-143">NAME</span><span class="sxs-lookup"><span data-stu-id="9017f-143">name</span></span>|<span data-ttu-id="9017f-144">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9017f-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9017f-145">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="9017f-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9017f-146">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="9017f-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9017f-147">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="9017f-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="9017f-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="9017f-148">openTimeout</span></span>|<span data-ttu-id="9017f-149"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9017f-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9017f-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9017f-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9017f-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9017f-151">The default is 00:01:00.</span></span>|
|<span data-ttu-id="9017f-152">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="9017f-152">privacyNoticeAt</span></span>|<span data-ttu-id="9017f-153">字串，指定隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="9017f-153">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="9017f-154">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="9017f-154">privacyNoticeVersion</span></span>|<span data-ttu-id="9017f-155">指定目前隱私權注意事項之版本的整數。</span><span class="sxs-lookup"><span data-stu-id="9017f-155">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="9017f-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="9017f-156">proxyAddress</span></span>|<span data-ttu-id="9017f-157">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="9017f-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="9017f-158">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9017f-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="9017f-159">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="9017f-159">The default is `null`.</span></span>|
|<span data-ttu-id="9017f-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="9017f-160">receiveTimeout</span></span>|<span data-ttu-id="9017f-161"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9017f-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9017f-162">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9017f-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9017f-163">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="9017f-163">The default is 00:10:00.</span></span>|
|<span data-ttu-id="9017f-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="9017f-164">sendTimeout</span></span>|<span data-ttu-id="9017f-165"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9017f-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9017f-166">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9017f-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9017f-167">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9017f-167">The default is 00:01:00.</span></span>|
|<span data-ttu-id="9017f-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="9017f-168">textEncoding</span></span>|<span data-ttu-id="9017f-169">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9017f-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="9017f-170">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="9017f-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9017f-171">BigEndianUnicodeUnicode BigEndian 編碼。</span><span class="sxs-lookup"><span data-stu-id="9017f-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="9017f-172">消除16位編碼。</span><span class="sxs-lookup"><span data-stu-id="9017f-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="9017f-173">UTF88位編碼</span><span class="sxs-lookup"><span data-stu-id="9017f-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="9017f-174">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="9017f-174">The default is UTF8.</span></span> <span data-ttu-id="9017f-175">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="9017f-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="9017f-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="9017f-176">transactionFlow</span></span>|<span data-ttu-id="9017f-177">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="9017f-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="9017f-178">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9017f-178">The default is `false`.</span></span>|
|<span data-ttu-id="9017f-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="9017f-179">useDefaultWebProxy</span></span>|<span data-ttu-id="9017f-180">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="9017f-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="9017f-181">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="9017f-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="9017f-182">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9017f-182">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9017f-183">子元素</span><span class="sxs-lookup"><span data-stu-id="9017f-183">Child Elements</span></span>

|<span data-ttu-id="9017f-184">項目</span><span class="sxs-lookup"><span data-stu-id="9017f-184">Element</span></span>|<span data-ttu-id="9017f-185">描述</span><span class="sxs-lookup"><span data-stu-id="9017f-185">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9017f-186">\<security></span><span class="sxs-lookup"><span data-stu-id="9017f-186">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="9017f-187">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9017f-187">Defines the security settings for the message.</span></span> <span data-ttu-id="9017f-188">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="9017f-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="9017f-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9017f-189">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="9017f-190">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="9017f-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9017f-191">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="9017f-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="9017f-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9017f-192">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="9017f-193">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="9017f-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9017f-194">父項目</span><span class="sxs-lookup"><span data-stu-id="9017f-194">Parent Elements</span></span>

|<span data-ttu-id="9017f-195">項目</span><span class="sxs-lookup"><span data-stu-id="9017f-195">Element</span></span>|<span data-ttu-id="9017f-196">描述</span><span class="sxs-lookup"><span data-stu-id="9017f-196">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9017f-197">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9017f-197">\<bindings></span></span>](bindings.md)|<span data-ttu-id="9017f-198">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="9017f-198">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9017f-199">備註</span><span class="sxs-lookup"><span data-stu-id="9017f-199">Remarks</span></span>

<span data-ttu-id="9017f-200">聯合是在多個系統上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="9017f-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="9017f-201">這些識別可以指向使用者或電腦。</span><span class="sxs-lookup"><span data-stu-id="9017f-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="9017f-202">聯合 HTTP 支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="9017f-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="9017f-203">此系結會提供 WS-同盟通訊協定的 Windows Communication Foundation （WCF）支援。</span><span class="sxs-lookup"><span data-stu-id="9017f-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="9017f-204">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="9017f-204">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="9017f-205">繫結是由繫結項目的堆疊組成。</span><span class="sxs-lookup"><span data-stu-id="9017f-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="9017f-206">位於</span><span class="sxs-lookup"><span data-stu-id="9017f-206">The stack of binding elements in</span></span>

<span data-ttu-id="9017f-207">`wsFederationHttpBinding` 與 `wsHttpBinding` 中包含的項目相同。</span><span class="sxs-lookup"><span data-stu-id="9017f-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="9017f-208">當[ \<安全性 >](security-of-wsfederationhttpbinding.md)設定為<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>的預設值時。</span><span class="sxs-lookup"><span data-stu-id="9017f-208">when [\<security>](security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="9017f-209">會控制 message [ \<>](message-element-of-wsfederationhttpbinding.md)中訊息安全性設定的詳細資料。 `wsFederationHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="9017f-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="9017f-210">請注意，[ [ \<安全性 >](security-of-wsfederationhttpbinding.md) ] 元素僅提供 [取得存取]，因為一旦建立系結之後，就無法變更系結所使用的安全性。</span><span class="sxs-lookup"><span data-stu-id="9017f-210">Note that the [\<security>](security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="9017f-211">`wsFederationHttpBinding`也會提供 privacyNoticeAt 屬性，以設定和抓取隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="9017f-211">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="9017f-212">維持原則的安全相當重要，特別是在聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="9017f-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="9017f-213">建議使用某種形式的安全性，例如 HTTPS，來保護原則不受惡意使用者攻擊。</span><span class="sxs-lookup"><span data-stu-id="9017f-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="9017f-214">在使用這個繫結的聯合案例中，服務原則可能有重要的資訊，例如用來加密所發行 (SAML) 權杖的金鑰、放入權杖內的宣告類型等等。</span><span class="sxs-lookup"><span data-stu-id="9017f-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="9017f-215">如果這個原則遭到竄改，攻擊者可能會發現可導致進一步竄改、資訊洩露和其他惡意行為的已發行權杖金鑰。</span><span class="sxs-lookup"><span data-stu-id="9017f-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="9017f-216">為了防止發生這種情況，必須安全地從服務取得原則 (例如，使用 HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="9017f-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="9017f-217">如需此系結的詳細資訊[，請參閱如何：建立 WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="9017f-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="9017f-218">範例</span><span class="sxs-lookup"><span data-stu-id="9017f-218">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9017f-219">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9017f-219">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="9017f-220">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9017f-220">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="9017f-221">繫結</span><span class="sxs-lookup"><span data-stu-id="9017f-221">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9017f-222">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9017f-222">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9017f-223">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="9017f-223">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9017f-224">\<binding></span><span class="sxs-lookup"><span data-stu-id="9017f-224">\<binding></span></span>](../../../misc/binding.md)
