---
title: <wsFederationHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: 8ed8f62f9415ed556a61ca53f27442a9355d8d7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698846"
---
# <a name="wsfederationhttpbinding"></a><span data-ttu-id="edb42-101">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="edb42-101">\<wsFederationHttpBinding></span></span>

<span data-ttu-id="edb42-102">定義支援 WS-Federation 的繫結。</span><span class="sxs-lookup"><span data-stu-id="edb42-102">Defines a binding that supports WS-Federation.</span></span>

<span data-ttu-id="edb42-103">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="edb42-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="edb42-104">\<bindings>\\</span><span class="sxs-lookup"><span data-stu-id="edb42-104">\<bindings>\\</span></span>
<span data-ttu-id="edb42-105">wsFederationBinding 項目</span><span class="sxs-lookup"><span data-stu-id="edb42-105">wsFederationBinding element</span></span>

## <a name="syntax"></a><span data-ttu-id="edb42-106">語法</span><span class="sxs-lookup"><span data-stu-id="edb42-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="edb42-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="edb42-107">Attributes and Elements</span></span>

<span data-ttu-id="edb42-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="edb42-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="edb42-109">屬性</span><span class="sxs-lookup"><span data-stu-id="edb42-109">Attributes</span></span>

|<span data-ttu-id="edb42-110">屬性</span><span class="sxs-lookup"><span data-stu-id="edb42-110">Attribute</span></span>|<span data-ttu-id="edb42-111">描述</span><span class="sxs-lookup"><span data-stu-id="edb42-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="edb42-112">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="edb42-112">bypassProxyOnLocal</span></span>|<span data-ttu-id="edb42-113">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="edb42-113">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="edb42-114">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="edb42-114">The default is `false`.</span></span>|
|<span data-ttu-id="edb42-115">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="edb42-115">closeTimeout</span></span>|<span data-ttu-id="edb42-116"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="edb42-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="edb42-117">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="edb42-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="edb42-118">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="edb42-118">The default is 00:01:00.</span></span>|
|<span data-ttu-id="edb42-119">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="edb42-119">hostnameComparisonMode</span></span>|<span data-ttu-id="edb42-120">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="edb42-120">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="edb42-121">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="edb42-121">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="edb42-122">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="edb42-122">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|<span data-ttu-id="edb42-123">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="edb42-123">maxBufferPoolSize</span></span>|<span data-ttu-id="edb42-124">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="edb42-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="edb42-125">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="edb42-125">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="edb42-126">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edb42-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="edb42-127">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="edb42-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="edb42-128">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="edb42-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="edb42-129">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="edb42-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|<span data-ttu-id="edb42-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="edb42-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="edb42-131">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="edb42-131">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="edb42-132">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="edb42-132">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="edb42-133">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="edb42-133">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="edb42-134">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="edb42-134">The default is 65536.</span></span>|
|<span data-ttu-id="edb42-135">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="edb42-135">messageEncoding</span></span>|<span data-ttu-id="edb42-136">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="edb42-136">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="edb42-137">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="edb42-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="edb42-138">文字：使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="edb42-138">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="edb42-139">Mtom:使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="edb42-139">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="edb42-140">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="edb42-140">The default is Text.</span></span><br /><br /> <span data-ttu-id="edb42-141">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="edb42-141">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|<span data-ttu-id="edb42-142">名稱</span><span class="sxs-lookup"><span data-stu-id="edb42-142">name</span></span>|<span data-ttu-id="edb42-143">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="edb42-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="edb42-144">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="edb42-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="edb42-145">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="edb42-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="edb42-146">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="edb42-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|<span data-ttu-id="edb42-147">openTimeout</span><span class="sxs-lookup"><span data-stu-id="edb42-147">openTimeout</span></span>|<span data-ttu-id="edb42-148"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="edb42-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="edb42-149">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="edb42-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="edb42-150">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="edb42-150">The default is 00:01:00.</span></span>|
|<span data-ttu-id="edb42-151">privacyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="edb42-151">privacyNoticeAt</span></span>|<span data-ttu-id="edb42-152">字串，指定隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="edb42-152">A String that specifies a URI at which the privacy notice is located.</span></span>|
|<span data-ttu-id="edb42-153">privacyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="edb42-153">privacyNoticeVersion</span></span>|<span data-ttu-id="edb42-154">指定目前隱私權注意事項之版本的整數。</span><span class="sxs-lookup"><span data-stu-id="edb42-154">An integer that specifies the version of the current privacy notice.</span></span>|
|<span data-ttu-id="edb42-155">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="edb42-155">proxyAddress</span></span>|<span data-ttu-id="edb42-156">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="edb42-156">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="edb42-157">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="edb42-157">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="edb42-158">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="edb42-158">The default is `null`.</span></span>|
|<span data-ttu-id="edb42-159">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="edb42-159">receiveTimeout</span></span>|<span data-ttu-id="edb42-160"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="edb42-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="edb42-161">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="edb42-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="edb42-162">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="edb42-162">The default is 00:10:00.</span></span>|
|<span data-ttu-id="edb42-163">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="edb42-163">sendTimeout</span></span>|<span data-ttu-id="edb42-164"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="edb42-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="edb42-165">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="edb42-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="edb42-166">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="edb42-166">The default is 00:01:00.</span></span>|
|<span data-ttu-id="edb42-167">textEncoding</span><span class="sxs-lookup"><span data-stu-id="edb42-167">textEncoding</span></span>|<span data-ttu-id="edb42-168">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="edb42-168">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="edb42-169">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="edb42-169">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="edb42-170">-BigEndianUnicode:Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="edb42-170">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="edb42-171">Unicode:16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="edb42-171">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="edb42-172">-UTF8:8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="edb42-172">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="edb42-173">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="edb42-173">The default is UTF8.</span></span> <span data-ttu-id="edb42-174">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="edb42-174">This attribute is of type <xref:System.Text.Encoding>..</span></span>|
|<span data-ttu-id="edb42-175">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="edb42-175">transactionFlow</span></span>|<span data-ttu-id="edb42-176">指定繫結程序是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="edb42-176">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="edb42-177">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="edb42-177">The default is `false`.</span></span>|
|<span data-ttu-id="edb42-178">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="edb42-178">useDefaultWebProxy</span></span>|<span data-ttu-id="edb42-179">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="edb42-179">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="edb42-180">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="edb42-180">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="edb42-181">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="edb42-181">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="edb42-182">子元素</span><span class="sxs-lookup"><span data-stu-id="edb42-182">Child Elements</span></span>

|<span data-ttu-id="edb42-183">項目</span><span class="sxs-lookup"><span data-stu-id="edb42-183">Element</span></span>|<span data-ttu-id="edb42-184">描述</span><span class="sxs-lookup"><span data-stu-id="edb42-184">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edb42-185">\<security></span><span class="sxs-lookup"><span data-stu-id="edb42-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="edb42-186">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="edb42-186">Defines the security settings for the message.</span></span> <span data-ttu-id="edb42-187">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="edb42-187">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="edb42-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="edb42-188">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="edb42-189">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="edb42-189">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="edb42-190">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="edb42-190">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="edb42-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="edb42-191">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="edb42-192">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="edb42-192">Specifies if reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="edb42-193">父項目</span><span class="sxs-lookup"><span data-stu-id="edb42-193">Parent Elements</span></span>

|<span data-ttu-id="edb42-194">項目</span><span class="sxs-lookup"><span data-stu-id="edb42-194">Element</span></span>|<span data-ttu-id="edb42-195">描述</span><span class="sxs-lookup"><span data-stu-id="edb42-195">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="edb42-196">\<bindings></span><span class="sxs-lookup"><span data-stu-id="edb42-196">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="edb42-197">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="edb42-197">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="edb42-198">備註</span><span class="sxs-lookup"><span data-stu-id="edb42-198">Remarks</span></span>

<span data-ttu-id="edb42-199">聯合是在多個系統上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="edb42-199">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="edb42-200">這些識別可以指向使用者或電腦。</span><span class="sxs-lookup"><span data-stu-id="edb42-200">These identities can refer to users or to machines.</span></span> <span data-ttu-id="edb42-201">聯合 HTTP 支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="edb42-201">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="edb42-202">這個繫結會提供 Windows Communication Foundation (WCF) 支援 WS-同盟通訊協定。</span><span class="sxs-lookup"><span data-stu-id="edb42-202">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="edb42-203">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="edb42-203">Services configured with this binding must use the HTTP transport.</span></span>

<span data-ttu-id="edb42-204">繫結是由繫結項目的堆疊組成。</span><span class="sxs-lookup"><span data-stu-id="edb42-204">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="edb42-205">位於</span><span class="sxs-lookup"><span data-stu-id="edb42-205">The stack of binding elements in</span></span>

<span data-ttu-id="edb42-206">`wsFederationHttpBinding` 與 `wsHttpBinding` 中包含的項目相同。</span><span class="sxs-lookup"><span data-stu-id="edb42-206">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>

<span data-ttu-id="edb42-207">當[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)設定的預設值為<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>。</span><span class="sxs-lookup"><span data-stu-id="edb42-207">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>

<span data-ttu-id="edb42-208">`wsFederationHttpBinding`控制項中的訊息安全性設定的詳細資料[\<訊息 >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="edb42-208">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="edb42-209">請注意， [\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)項目提供存取權，只有在建立繫結之後，就無法變更繫結所使用的安全性。</span><span class="sxs-lookup"><span data-stu-id="edb42-209">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>

<span data-ttu-id="edb42-210">`wsFederationHttpBinding`也提供 privacyNoticeAt 屬性來設定和擷取隱私權注意事項所在 URI。</span><span class="sxs-lookup"><span data-stu-id="edb42-210">The `wsFederationHttpBinding` also provides a privacyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>

<span data-ttu-id="edb42-211">維持原則的安全相當重要，特別是在聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="edb42-211">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="edb42-212">建議使用某種形式的安全性，例如 HTTPS，來保護原則不受惡意使用者攻擊。</span><span class="sxs-lookup"><span data-stu-id="edb42-212">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>

<span data-ttu-id="edb42-213">在使用這個繫結的聯合案例中，服務原則可能有重要的資訊，例如用來加密所發行 (SAML) 權杖的金鑰、放入權杖內的宣告類型等等。</span><span class="sxs-lookup"><span data-stu-id="edb42-213">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="edb42-214">如果這個原則遭到竄改，攻擊者可能會發現可導致進一步竄改、資訊洩露和其他惡意行為的已發行權杖金鑰。</span><span class="sxs-lookup"><span data-stu-id="edb42-214">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="edb42-215">為了防止發生這種情況，必須安全地從服務取得原則 (例如，使用 HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="edb42-215">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>

<span data-ttu-id="edb42-216">如需有關這個繫結的詳細資訊，請參閱[How to:建立 WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="edb42-216">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="edb42-217">範例</span><span class="sxs-lookup"><span data-stu-id="edb42-217">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="edb42-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edb42-218">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>
- [<span data-ttu-id="edb42-219">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="edb42-219">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="edb42-220">繫結</span><span class="sxs-lookup"><span data-stu-id="edb42-220">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="edb42-221">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="edb42-221">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="edb42-222">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="edb42-222">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="edb42-223">\<binding></span><span class="sxs-lookup"><span data-stu-id="edb42-223">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
