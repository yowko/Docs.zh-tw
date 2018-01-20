---
title: '&lt;wsFederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5d4e55f7ad2d4a347d51c3cd79647c070c11e2d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="03b18-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="03b18-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="03b18-103">定義支援 WS-Federation 的繫結。</span><span class="sxs-lookup"><span data-stu-id="03b18-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="03b18-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="03b18-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="03b18-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="03b18-105">\<bindings></span></span>  
<span data-ttu-id="03b18-106">wsFederationBinding 項目</span><span class="sxs-lookup"><span data-stu-id="03b18-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b18-107">語法</span><span class="sxs-lookup"><span data-stu-id="03b18-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
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
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
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
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b18-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03b18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="03b18-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="03b18-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b18-110">屬性</span><span class="sxs-lookup"><span data-stu-id="03b18-110">Attributes</span></span>  
  
|<span data-ttu-id="03b18-111">屬性</span><span class="sxs-lookup"><span data-stu-id="03b18-111">Attribute</span></span>|<span data-ttu-id="03b18-112">描述</span><span class="sxs-lookup"><span data-stu-id="03b18-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03b18-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="03b18-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="03b18-114">布林值，指出本機位址是否略過 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="03b18-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="03b18-115">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="03b18-115">The default is `false`.</span></span>|  
|<span data-ttu-id="03b18-116">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="03b18-116">closeTimeout</span></span>|<span data-ttu-id="03b18-117"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="03b18-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="03b18-118">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="03b18-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03b18-119">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="03b18-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="03b18-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="03b18-120">hostnameComparisonMode</span></span>|<span data-ttu-id="03b18-121">指定用於剖析 URI 的 HTTP 主機名稱比較模式。</span><span class="sxs-lookup"><span data-stu-id="03b18-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="03b18-122">這個屬性的型別為 <xref:System.ServiceModel.HostNameComparisonMode>，表示比對 URI 時此主機名稱是否會用來取用服務。</span><span class="sxs-lookup"><span data-stu-id="03b18-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="03b18-123">預設值為 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示比對時忽略主機名稱。</span><span class="sxs-lookup"><span data-stu-id="03b18-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="03b18-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="03b18-124">maxBufferPoolSize</span></span>|<span data-ttu-id="03b18-125">指定此繫結之緩衝區集區大小上限的整數。</span><span class="sxs-lookup"><span data-stu-id="03b18-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="03b18-126">預設為 524,288 個位元組 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="03b18-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="03b18-127">Windows Communication Foundation (WCF) 的許多部分會使用緩衝區。</span><span class="sxs-lookup"><span data-stu-id="03b18-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="03b18-128">每次使用這些組件時建立並終結緩衝區是高度耗費資源的作業，回收緩衝區的記憶體也是如此。</span><span class="sxs-lookup"><span data-stu-id="03b18-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="03b18-129">有了緩衝集區，您就可以從集區取出緩衝區來使用，用完後再還給集區，</span><span class="sxs-lookup"><span data-stu-id="03b18-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="03b18-130">因此可以避免建立及終結緩衝區的負荷。</span><span class="sxs-lookup"><span data-stu-id="03b18-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="03b18-131">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="03b18-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="03b18-132">正整數，指定在使用此繫結設定之通道上可以接收的訊息大小上限 (以位元組為單位，包括標頭)。</span><span class="sxs-lookup"><span data-stu-id="03b18-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="03b18-133">超出此限制之訊息的寄件者將會收到 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="03b18-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="03b18-134">收件者會捨棄訊息，然後在追蹤記錄檔中建立此事件的項目。</span><span class="sxs-lookup"><span data-stu-id="03b18-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="03b18-135">預設值為 65536。</span><span class="sxs-lookup"><span data-stu-id="03b18-135">The default is 65536.</span></span>|  
|<span data-ttu-id="03b18-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="03b18-136">messageEncoding</span></span>|<span data-ttu-id="03b18-137">定義用來對訊息進行編碼的編碼器。</span><span class="sxs-lookup"><span data-stu-id="03b18-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="03b18-138">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="03b18-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="03b18-139">檢索： 使用文字訊息編碼器。</span><span class="sxs-lookup"><span data-stu-id="03b18-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="03b18-140">Mtom： 使用訊息傳輸 Organization Mechanism 1.0 (MTOM) 編碼器。</span><span class="sxs-lookup"><span data-stu-id="03b18-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="03b18-141">預設為 Text。</span><span class="sxs-lookup"><span data-stu-id="03b18-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="03b18-142">此屬性的型別為 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="03b18-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="03b18-143">name</span><span class="sxs-lookup"><span data-stu-id="03b18-143">name</span></span>|<span data-ttu-id="03b18-144">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="03b18-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="03b18-145">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="03b18-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="03b18-146">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="03b18-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="03b18-147">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="03b18-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="03b18-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="03b18-148">openTimeout</span></span>|<span data-ttu-id="03b18-149"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="03b18-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="03b18-150">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="03b18-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03b18-151">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="03b18-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="03b18-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="03b18-152">privactyNoticeAt</span></span>|<span data-ttu-id="03b18-153">字串，指定隱私權注意事項所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="03b18-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="03b18-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="03b18-154">privactyNoticeVersion</span></span>|<span data-ttu-id="03b18-155">指定目前隱私權注意事項之版本的整數。</span><span class="sxs-lookup"><span data-stu-id="03b18-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="03b18-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="03b18-156">proxyAddress</span></span>|<span data-ttu-id="03b18-157">指定 HTTP Proxy 位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="03b18-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="03b18-158">如果 `useDefaultWebProxy` 為 `true`，則這項設定必須為 `null`。</span><span class="sxs-lookup"><span data-stu-id="03b18-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="03b18-159">預設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="03b18-159">The default is `null`.</span></span>|  
|<span data-ttu-id="03b18-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="03b18-160">receiveTimeout</span></span>|<span data-ttu-id="03b18-161"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="03b18-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="03b18-162">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="03b18-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03b18-163">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="03b18-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="03b18-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="03b18-164">sendTimeout</span></span>|<span data-ttu-id="03b18-165"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="03b18-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="03b18-166">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="03b18-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="03b18-167">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="03b18-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="03b18-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="03b18-168">textEncoding</span></span>|<span data-ttu-id="03b18-169">設定要在繫結上發出訊息時使用的字元集編碼方式。</span><span class="sxs-lookup"><span data-stu-id="03b18-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="03b18-170">有效值包括以下的值：</span><span class="sxs-lookup"><span data-stu-id="03b18-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="03b18-171">-BigEndianUnicode: Unicode BigEndian 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="03b18-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="03b18-172">Unicode: 16 位元編碼方式。</span><span class="sxs-lookup"><span data-stu-id="03b18-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="03b18-173">UTF8: 8 位元編碼</span><span class="sxs-lookup"><span data-stu-id="03b18-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="03b18-174">預設為 UTF8。</span><span class="sxs-lookup"><span data-stu-id="03b18-174">The default is UTF8.</span></span> <span data-ttu-id="03b18-175">此屬性的型別為 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="03b18-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="03b18-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="03b18-176">transactionFlow</span></span>|<span data-ttu-id="03b18-177">指定繫結是否支援流動 WS-Transactions 的布林值。</span><span class="sxs-lookup"><span data-stu-id="03b18-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="03b18-178">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="03b18-178">The default is `false`.</span></span>|  
|<span data-ttu-id="03b18-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="03b18-179">useDefaultWebProxy</span></span>|<span data-ttu-id="03b18-180">布林值，指定是否使用系統自動設定的 HTTP Proxy。</span><span class="sxs-lookup"><span data-stu-id="03b18-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="03b18-181">如果這個屬性為 `null`，則 Proxy 位址必須為 `true` (也就是不設定)。</span><span class="sxs-lookup"><span data-stu-id="03b18-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="03b18-182">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="03b18-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03b18-183">子元素</span><span class="sxs-lookup"><span data-stu-id="03b18-183">Child Elements</span></span>  
  
|<span data-ttu-id="03b18-184">項目</span><span class="sxs-lookup"><span data-stu-id="03b18-184">Element</span></span>|<span data-ttu-id="03b18-185">描述</span><span class="sxs-lookup"><span data-stu-id="03b18-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b18-186">\<security></span><span class="sxs-lookup"><span data-stu-id="03b18-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="03b18-187">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="03b18-187">Defines the security settings for the message.</span></span> <span data-ttu-id="03b18-188">此項目的型別為 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="03b18-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="03b18-189">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="03b18-189">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="03b18-190">定義 SOAP 訊息複雜度的條件約束，而這些條件約束可由以此繫結所設定的端點處理。</span><span class="sxs-lookup"><span data-stu-id="03b18-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="03b18-191">此項目的型別為 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="03b18-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="03b18-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="03b18-192">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="03b18-193">指定是否在通道端點之間建立可靠的工作階段。</span><span class="sxs-lookup"><span data-stu-id="03b18-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03b18-194">父項目</span><span class="sxs-lookup"><span data-stu-id="03b18-194">Parent Elements</span></span>  
  
|<span data-ttu-id="03b18-195">項目</span><span class="sxs-lookup"><span data-stu-id="03b18-195">Element</span></span>|<span data-ttu-id="03b18-196">描述</span><span class="sxs-lookup"><span data-stu-id="03b18-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03b18-197">\<bindings></span><span class="sxs-lookup"><span data-stu-id="03b18-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="03b18-198">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="03b18-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b18-199">備註</span><span class="sxs-lookup"><span data-stu-id="03b18-199">Remarks</span></span>  
 <span data-ttu-id="03b18-200">聯合是在多個系統上共用識別以便進行驗證和授權的能力。</span><span class="sxs-lookup"><span data-stu-id="03b18-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="03b18-201">這些識別可以指向使用者或電腦。</span><span class="sxs-lookup"><span data-stu-id="03b18-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="03b18-202">聯合 HTTP 支援 SOAP 安全性以及混合模式安全性，但不支援獨立使用傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="03b18-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="03b18-203">這個繫結提供 WS-Federation 通訊協定的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="03b18-203">This binding provides [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] support for the WS-Federation protocol.</span></span> <span data-ttu-id="03b18-204">使用這個繫結設定的服務必須使用 HTTP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="03b18-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="03b18-205">繫結是由繫結項目的堆疊組成。</span><span class="sxs-lookup"><span data-stu-id="03b18-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="03b18-206">位於</span><span class="sxs-lookup"><span data-stu-id="03b18-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="03b18-207">`wsFederationHttpBinding` 與 `wsHttpBinding` 中包含的項目相同。</span><span class="sxs-lookup"><span data-stu-id="03b18-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="03b18-208">當[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)設定的預設值為<xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>。</span><span class="sxs-lookup"><span data-stu-id="03b18-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="03b18-209">`wsFederationHttpBinding`控制項中的訊息安全性設定的詳細資料[\<訊息 >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="03b18-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="03b18-210">請注意， [\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)元素提供存取，只有在建立繫結之後，就無法變更繫結所使用的安全性。</span><span class="sxs-lookup"><span data-stu-id="03b18-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="03b18-211">`wsFederationHttpBinding` 也會提供 privactyNoticeAt 屬性，在隱私權注意事項所在的位置設定及擷取 URI。</span><span class="sxs-lookup"><span data-stu-id="03b18-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="03b18-212">維持原則的安全相當重要，特別是在聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="03b18-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="03b18-213">建議使用某種形式的安全性，例如 HTTPS，來保護原則不受惡意使用者攻擊。</span><span class="sxs-lookup"><span data-stu-id="03b18-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="03b18-214">在使用這個繫結的聯合案例中，服務原則可能有重要的資訊，例如用來加密所發行 (SAML) 權杖的金鑰、放入權杖內的宣告類型等等。</span><span class="sxs-lookup"><span data-stu-id="03b18-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="03b18-215">如果這個原則遭到竄改，攻擊者可能會發現可導致進一步竄改、資訊洩露和其他惡意行為的已發行權杖金鑰。</span><span class="sxs-lookup"><span data-stu-id="03b18-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="03b18-216">為了防止發生這種情況，必須安全地從服務取得原則 (例如，使用 HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="03b18-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="03b18-217">如需有關這個繫結的詳細資訊，請參閱[How to： 建立 WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="03b18-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b18-218">範例</span><span class="sxs-lookup"><span data-stu-id="03b18-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
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
  
## <a name="see-also"></a><span data-ttu-id="03b18-219">請參閱</span><span class="sxs-lookup"><span data-stu-id="03b18-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="03b18-220">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="03b18-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="03b18-221">繫結</span><span class="sxs-lookup"><span data-stu-id="03b18-221">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="03b18-222">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="03b18-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="03b18-223">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="03b18-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="03b18-224">\<binding></span><span class="sxs-lookup"><span data-stu-id="03b18-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
