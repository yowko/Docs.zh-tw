---
title: '&lt;customBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
ms.openlocfilehash: 741f195a78c1716b95d8d4d88594207708ce6289
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123822"
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="a3dac-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a3dac-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="a3dac-103">對使用者提供訊息堆疊的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="a3dac-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="a3dac-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a3dac-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a3dac-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a3dac-105">\<bindings></span></span>  
<span data-ttu-id="a3dac-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a3dac-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3dac-107">語法</span><span class="sxs-lookup"><span data-stu-id="a3dac-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           authenticationMode="UserNameForAnonymous"  
           contextMode="Cookie"   
           defaultProtectionLevel="Sign"  
           enableKeyDerivation="false"  
           keyEntropyMode="ClientEntropy"   
                  messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"   
           securityVersion="WSSecurityXXX2005">  
           <localClientSettings cacheCookies="false"  
               detectReplays="false"  
               maxCookieCachingTime="00:07:24" />  
           <localServiceSettings replayCacheSize="9"  
               maxClockSkew="00:00:03"   
               replayWindow="00:07:22.2190000" />  
       </security>  
       <binaryMessageEncoding maxReadPoolSize="Integer"  
           maxWritePoolSize="Integer"  
           maxSessionSize="Integer" />  
       <httpsTransport manualAddressing="Boolean"  
           maxMessageSize="Integer"  
           authenticationScheme="Negotiate"   
           bypassProxyOnLocal="Boolean"  
           hostNameComparisonMode="Exact"   
           mapAddressingHeadersToHttpHeaders="Boolean"   
           proxyaddress="Uri"  
           realm="String"   
           requireClientCertificate="Boolean" />  
       <peerTransport manualAddressing="false"  
          maxMessageSize="20002"  
          listenIPAddress="202.10.1.9"   
          messageAuthentication="false"  
          peerNodeAuthenticationMode="None"  
          port="1000" />  
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3dac-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3dac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a3dac-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a3dac-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3dac-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a3dac-110">Attributes</span></span>  
  
|<span data-ttu-id="a3dac-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a3dac-111">Attribute</span></span>|<span data-ttu-id="a3dac-112">描述</span><span class="sxs-lookup"><span data-stu-id="a3dac-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3dac-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a3dac-113">closeTimeout</span></span>|<span data-ttu-id="a3dac-114"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a3dac-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a3dac-115">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a3dac-116">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a3dac-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a3dac-117">name</span><span class="sxs-lookup"><span data-stu-id="a3dac-117">name</span></span>|<span data-ttu-id="a3dac-118">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a3dac-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a3dac-119">這個值是使用者定義的字串，它會充當自訂繫結的識別字串。</span><span class="sxs-lookup"><span data-stu-id="a3dac-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="a3dac-120">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="a3dac-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a3dac-121">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a3dac-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="a3dac-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a3dac-122">openTimeout</span></span>|<span data-ttu-id="a3dac-123"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a3dac-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a3dac-124">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a3dac-125">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a3dac-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a3dac-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a3dac-126">receiveTimeout</span></span>|<span data-ttu-id="a3dac-127"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a3dac-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a3dac-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a3dac-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a3dac-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="a3dac-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="a3dac-130">sendTimeout</span></span>|<span data-ttu-id="a3dac-131"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a3dac-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a3dac-132">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a3dac-133">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a3dac-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3dac-134">子元素</span><span class="sxs-lookup"><span data-stu-id="a3dac-134">Child Elements</span></span>  
  
|<span data-ttu-id="a3dac-135">項目</span><span class="sxs-lookup"><span data-stu-id="a3dac-135">Element</span></span>|<span data-ttu-id="a3dac-136">描述</span><span class="sxs-lookup"><span data-stu-id="a3dac-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3dac-137">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="a3dac-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="a3dac-138">指定自訂繫結的雙向傳訊。</span><span class="sxs-lookup"><span data-stu-id="a3dac-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="a3dac-139">它是和本身不允許雙工通訊的傳輸一起使用，例如 HTTP。</span><span class="sxs-lookup"><span data-stu-id="a3dac-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="a3dac-140">相反地，TCP 本身就允許雙工通訊，因此不需要使用這個繫結項目也可讓服務將訊息傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="a3dac-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="a3dac-141">用戶端必須公開位址，才能讓服務接觸並建立連接。</span><span class="sxs-lookup"><span data-stu-id="a3dac-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="a3dac-142">這個用戶端位址是由 `ClientBaseAddress` 屬性提供。</span><span class="sxs-lookup"><span data-stu-id="a3dac-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="a3dac-143">此項目的型別為 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="a3dac-144">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="a3dac-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="a3dac-145">指定對等名稱解析通訊協定 (PNRP) 對等名稱解析程式。</span><span class="sxs-lookup"><span data-stu-id="a3dac-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="a3dac-146">此項目的型別為 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="a3dac-147">\<reliableSession></span><span class="sxs-lookup"><span data-stu-id="a3dac-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="a3dac-148">指定 WS-Reliable 訊息設定。</span><span class="sxs-lookup"><span data-stu-id="a3dac-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="a3dac-149">將這個項目新增至自訂繫結時，產生的通道可支援確實傳送一次保證。</span><span class="sxs-lookup"><span data-stu-id="a3dac-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="a3dac-150">此項目的型別為 <xref:System.ServiceModel.Configuration.ReliableSessionElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="a3dac-151">\<security></span><span class="sxs-lookup"><span data-stu-id="a3dac-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="a3dac-152">指定自訂繫結的安全性選項。</span><span class="sxs-lookup"><span data-stu-id="a3dac-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="a3dac-153">此項目的型別為 <xref:System.ServiceModel.Configuration.SecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="a3dac-154">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a3dac-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="a3dac-155">指定 SSL 資料流繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="a3dac-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="a3dac-156">此項目的型別為 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="a3dac-157">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="a3dac-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="a3dac-158">指定繫結應支援交易流程，並指定 `transactionProtocol` 屬性使用的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a3dac-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="a3dac-159">此項目的型別為 <xref:System.ServiceModel.Configuration.TransactionFlowElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="a3dac-160">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a3dac-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="a3dac-161">指定自訂繫結的資料流 (Streaming) 安全性選項。</span><span class="sxs-lookup"><span data-stu-id="a3dac-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="a3dac-162">此項目的型別為 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3dac-163">父項目</span><span class="sxs-lookup"><span data-stu-id="a3dac-163">Parent Elements</span></span>  
  
|<span data-ttu-id="a3dac-164">項目</span><span class="sxs-lookup"><span data-stu-id="a3dac-164">Element</span></span>|<span data-ttu-id="a3dac-165">描述</span><span class="sxs-lookup"><span data-stu-id="a3dac-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3dac-166">繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-166">bindings</span></span>|<span data-ttu-id="a3dac-167">包含 Windows Communication Foundation 應用程式的所有繫結。</span><span class="sxs-lookup"><span data-stu-id="a3dac-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3dac-168">備註</span><span class="sxs-lookup"><span data-stu-id="a3dac-168">Remarks</span></span>  
 <span data-ttu-id="a3dac-169">自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="a3dac-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a3dac-170">您可以新增特定實體的組態項目，來建立特別量身訂作的繫結。</span><span class="sxs-lookup"><span data-stu-id="a3dac-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="a3dac-171">例如，使用者可結合 `httpsTransport` 區段、`reliableSession` 區段和 `security` 區段來建立可靠且安全的 https 繫結。</span><span class="sxs-lookup"><span data-stu-id="a3dac-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="a3dac-172">個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。</span><span class="sxs-lookup"><span data-stu-id="a3dac-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a3dac-173">每個項目都會定義及設定堆疊的一個項目。</span><span class="sxs-lookup"><span data-stu-id="a3dac-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a3dac-174">各個自訂繫結中一定要出現一個而且是唯一一個的傳輸項目。</span><span class="sxs-lookup"><span data-stu-id="a3dac-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="a3dac-175">如果沒有這個項目，訊息堆疊就不完整。</span><span class="sxs-lookup"><span data-stu-id="a3dac-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a3dac-176">項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="a3dac-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a3dac-177">建議的堆疊項目順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3dac-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a3dac-178">交易 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="a3dac-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a3dac-179">可信賴傳訊 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="a3dac-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a3dac-180">安全性 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="a3dac-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a3dac-181">Transport</span><span class="sxs-lookup"><span data-stu-id="a3dac-181">Transport</span></span>  
  
5.  <span data-ttu-id="a3dac-182">編碼器 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="a3dac-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="a3dac-183">當系統提供的其中一個繫結不符合服務的需求時，請使用自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="a3dac-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="a3dac-184">例如，若要在服務端點上啟用新的傳輸或新的編碼器，可以使用自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="a3dac-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="a3dac-185">在建構自訂繫結時，會使用依據特定順序堆疊之繫結項目集合中的其中一個 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A>：</span><span class="sxs-lookup"><span data-stu-id="a3dac-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="a3dac-186">在最上方為允許流動交易的選擇性 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="a3dac-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="a3dac-187">接下來是選擇性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>，它會提供 WS-ReliableMessaging 規格中所定義的工作階段和排序機制。</span><span class="sxs-lookup"><span data-stu-id="a3dac-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="a3dac-188">這個工作階段概念可以跨越 SOAP 和傳輸媒介。</span><span class="sxs-lookup"><span data-stu-id="a3dac-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="a3dac-189">接下來是選擇性安全性繫結項目，它會提供類似授權、驗證 (Authentication)、保護和機密性等安全性功能。</span><span class="sxs-lookup"><span data-stu-id="a3dac-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="a3dac-190">Windows Communication Foundation (WCF) 提供下列安全性繫結項目：</span><span class="sxs-lookup"><span data-stu-id="a3dac-190">The following security binding elements are provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="a3dac-191">接下來是繫結項目所指定的選擇性訊息模式：</span><span class="sxs-lookup"><span data-stu-id="a3dac-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="a3dac-192">接下來是選擇性傳輸升級/helper 繫結項目：</span><span class="sxs-lookup"><span data-stu-id="a3dac-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="a3dac-193">再來是必要的訊息編碼繫結項目。</span><span class="sxs-lookup"><span data-stu-id="a3dac-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="a3dac-194">您可以使用自己的傳輸或是使用下列其中一個訊息編碼繫結：</span><span class="sxs-lookup"><span data-stu-id="a3dac-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="a3dac-195">最下方是必要的傳輸項目。</span><span class="sxs-lookup"><span data-stu-id="a3dac-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="a3dac-196">您可以使用自己的傳輸，或使用其中一個傳輸繫結提供由 Windows Communication Foundation (WCF) 的項目：</span><span class="sxs-lookup"><span data-stu-id="a3dac-196">You can use your own transport or use one of transport binding elements provided by Windows Communication Foundation (WCF):</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="a3dac-197">下表摘要列出每一層的選項。</span><span class="sxs-lookup"><span data-stu-id="a3dac-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="a3dac-198">圖層</span><span class="sxs-lookup"><span data-stu-id="a3dac-198">Layer</span></span>|<span data-ttu-id="a3dac-199">選項</span><span class="sxs-lookup"><span data-stu-id="a3dac-199">Options</span></span>|<span data-ttu-id="a3dac-200">必要項</span><span class="sxs-lookup"><span data-stu-id="a3dac-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="a3dac-201">交易流程</span><span class="sxs-lookup"><span data-stu-id="a3dac-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="a3dac-202">否</span><span class="sxs-lookup"><span data-stu-id="a3dac-202">No</span></span>|  
|<span data-ttu-id="a3dac-203">可靠性</span><span class="sxs-lookup"><span data-stu-id="a3dac-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="a3dac-204">否</span><span class="sxs-lookup"><span data-stu-id="a3dac-204">No</span></span>|  
|<span data-ttu-id="a3dac-205">安全性</span><span class="sxs-lookup"><span data-stu-id="a3dac-205">Security</span></span>|<span data-ttu-id="a3dac-206">對稱、不對稱、傳輸層級</span><span class="sxs-lookup"><span data-stu-id="a3dac-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="a3dac-207">否</span><span class="sxs-lookup"><span data-stu-id="a3dac-207">No</span></span>|  
|<span data-ttu-id="a3dac-208">形狀變更</span><span class="sxs-lookup"><span data-stu-id="a3dac-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="a3dac-209">否</span><span class="sxs-lookup"><span data-stu-id="a3dac-209">No</span></span>|  
|<span data-ttu-id="a3dac-210">傳輸升級</span><span class="sxs-lookup"><span data-stu-id="a3dac-210">Transport Upgrades</span></span>|<span data-ttu-id="a3dac-211">SSL 資料流、Windows 資料流、對等解析程式</span><span class="sxs-lookup"><span data-stu-id="a3dac-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="a3dac-212">否</span><span class="sxs-lookup"><span data-stu-id="a3dac-212">No</span></span>|  
|<span data-ttu-id="a3dac-213">編碼</span><span class="sxs-lookup"><span data-stu-id="a3dac-213">Encoding</span></span>|<span data-ttu-id="a3dac-214">文字、二進位、MTOM、自訂</span><span class="sxs-lookup"><span data-stu-id="a3dac-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="a3dac-215">是</span><span class="sxs-lookup"><span data-stu-id="a3dac-215">Yes</span></span>|  
|<span data-ttu-id="a3dac-216">Transport</span><span class="sxs-lookup"><span data-stu-id="a3dac-216">Transport</span></span>|<span data-ttu-id="a3dac-217">TCP、具名管道、HTTP、HTTPS、MSMQ 的類別、自訂</span><span class="sxs-lookup"><span data-stu-id="a3dac-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="a3dac-218">是</span><span class="sxs-lookup"><span data-stu-id="a3dac-218">Yes</span></span>|  
  
 <span data-ttu-id="a3dac-219">此外，您也可以定義自己的繫結項目，並將其插入上述任何定義層之間。</span><span class="sxs-lookup"><span data-stu-id="a3dac-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="a3dac-220">如需如何使用自訂繫結來修改系統提供繫結的討論，請參閱 <<c0> [ 如何： 自訂之繫結](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="a3dac-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="a3dac-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3dac-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a3dac-222">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a3dac-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="a3dac-223">繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-223">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a3dac-224">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a3dac-225">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a3dac-226">customBinding 元素</span><span class="sxs-lookup"><span data-stu-id="a3dac-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a3dac-227">繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-227">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a3dac-228">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a3dac-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a3dac-229">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a3dac-229">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
