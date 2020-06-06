---
title: <messageSenderAuthentication> 項目
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397781"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="d3c1e-102">\<messageSenderAuthentication> 項目</span><span class="sxs-lookup"><span data-stu-id="d3c1e-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="d3c1e-103">指定對等訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="d3c1e-104">如需對等程式設計的詳細資訊，請參閱[對等網路](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="d3c1e-105">語法</span><span class="sxs-lookup"><span data-stu-id="d3c1e-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3c1e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3c1e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d3c1e-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d3c1e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3c1e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-108">Attributes</span></span>  
  
|<span data-ttu-id="d3c1e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-109">Attribute</span></span>|<span data-ttu-id="d3c1e-110">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="d3c1e-111">用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="d3c1e-112">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="d3c1e-113">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="d3c1e-114">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="d3c1e-115">用於檢查撤銷憑證清單 (CRL) 的模式之一。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="d3c1e-116">兩個系統存放位置的其中一個：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="d3c1e-117">當與用戶端交涉服務憑證時，會使用這個值。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="d3c1e-118">會針對指定存放區位置中的「**受信任的人**」存放區執行驗證。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="d3c1e-119">customCertificateValidatorType 屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="d3c1e-120">值</span><span class="sxs-lookup"><span data-stu-id="d3c1e-120">Value</span></span>|<span data-ttu-id="d3c1e-121">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3c1e-122">字串</span><span class="sxs-lookup"><span data-stu-id="d3c1e-122">String</span></span>|<span data-ttu-id="d3c1e-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-123">Optional.</span></span> <span data-ttu-id="d3c1e-124">指定型別名稱和組件以及用來尋找此型別的其他資料。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="d3c1e-125">至少需要命名空間和型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="d3c1e-126">選擇性的資訊包括：組件名稱、版本號碼、文化特性和公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="d3c1e-127">certificateValidationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="d3c1e-128">值</span><span class="sxs-lookup"><span data-stu-id="d3c1e-128">Value</span></span>|<span data-ttu-id="d3c1e-129">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3c1e-130">列舉型別</span><span class="sxs-lookup"><span data-stu-id="d3c1e-130">Enumeration</span></span>|<span data-ttu-id="d3c1e-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-131">Optional.</span></span> <span data-ttu-id="d3c1e-132">下列其中一個值：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="d3c1e-133">預設值為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="d3c1e-134">預設值為 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="d3c1e-135">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="d3c1e-136">revocationMode 屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="d3c1e-137">值</span><span class="sxs-lookup"><span data-stu-id="d3c1e-137">Value</span></span>|<span data-ttu-id="d3c1e-138">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3c1e-139">列舉型別</span><span class="sxs-lookup"><span data-stu-id="d3c1e-139">Enumeration</span></span>|<span data-ttu-id="d3c1e-140">下列其中一個值：`NoCheck`、`Online`、`Offline`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="d3c1e-141">預設值為 `Online`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="d3c1e-142">如需詳細資訊，請參閱[使用憑證](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="d3c1e-143">trustedStoreLocation 屬性</span><span class="sxs-lookup"><span data-stu-id="d3c1e-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="d3c1e-144">值</span><span class="sxs-lookup"><span data-stu-id="d3c1e-144">Value</span></span>|<span data-ttu-id="d3c1e-145">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3c1e-146">列舉型別</span><span class="sxs-lookup"><span data-stu-id="d3c1e-146">Enumeration</span></span>|<span data-ttu-id="d3c1e-147">下列其中一個值：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="d3c1e-148">預設值為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="d3c1e-149">如果用戶端應用程式是在系統帳戶下執行，則憑證通常位於 `LocalMachine` 之下。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="d3c1e-150">如果用戶端應用程式是在使用者帳戶下執行，則憑證通常位於 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="d3c1e-151">預設值為 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3c1e-152">子元素</span><span class="sxs-lookup"><span data-stu-id="d3c1e-152">Child Elements</span></span>  
 <span data-ttu-id="d3c1e-153">無。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3c1e-154">父項目</span><span class="sxs-lookup"><span data-stu-id="d3c1e-154">Parent Elements</span></span>  
  
|<span data-ttu-id="d3c1e-155">元素</span><span class="sxs-lookup"><span data-stu-id="d3c1e-155">Element</span></span>|<span data-ttu-id="d3c1e-156">描述</span><span class="sxs-lookup"><span data-stu-id="d3c1e-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="d3c1e-157">指定向對等服務驗證用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c1e-158">備註</span><span class="sxs-lookup"><span data-stu-id="d3c1e-158">Remarks</span></span>  
 <span data-ttu-id="d3c1e-159">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="d3c1e-160">針對輸出通道，每個訊息都是使用所提供的憑證來簽署 [\<certificate>](certificate-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="d3c1e-161">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="d3c1e-162">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3c1e-163">範例</span><span class="sxs-lookup"><span data-stu-id="d3c1e-163">Example</span></span>  
 <span data-ttu-id="d3c1e-164">下列程式碼會將訊息寄件者驗證模式設定為 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="d3c1e-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="d3c1e-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c1e-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="d3c1e-166">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="d3c1e-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d3c1e-167">對等網路</span><span class="sxs-lookup"><span data-stu-id="d3c1e-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="d3c1e-168">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d3c1e-168">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="d3c1e-169">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d3c1e-169">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="d3c1e-170">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="d3c1e-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
