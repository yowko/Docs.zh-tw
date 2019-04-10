---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: b8643a5321bbab692ebb704101c664105b4ab55c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162185"
---
# <a name="messagesenderauthentication"></a><span data-ttu-id="432bc-101">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="432bc-101">\<messageSenderAuthentication></span></span>
<span data-ttu-id="432bc-102">為訊息寄件者使用的對等憑證指定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="432bc-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="432bc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="432bc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="432bc-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="432bc-104">\<behaviors></span></span>  
<span data-ttu-id="432bc-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="432bc-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="432bc-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="432bc-106">\<behavior></span></span>  
<span data-ttu-id="432bc-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="432bc-107">\<serviceCredentials></span></span>  
<span data-ttu-id="432bc-108">\<peer></span><span class="sxs-lookup"><span data-stu-id="432bc-108">\<peer></span></span>  
<span data-ttu-id="432bc-109">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="432bc-109">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432bc-110">語法</span><span class="sxs-lookup"><span data-stu-id="432bc-110">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="432bc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="432bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="432bc-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="432bc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="432bc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="432bc-113">Attributes</span></span>  
  
|<span data-ttu-id="432bc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="432bc-114">Attribute</span></span>|<span data-ttu-id="432bc-115">描述</span><span class="sxs-lookup"><span data-stu-id="432bc-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="432bc-116">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="432bc-116">Optional enumeration.</span></span> <span data-ttu-id="432bc-117">指定用來驗證認證的五個模式之一。</span><span class="sxs-lookup"><span data-stu-id="432bc-117">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="432bc-118">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="432bc-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="432bc-119">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="432bc-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="432bc-120">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="432bc-120">Optional string.</span></span> <span data-ttu-id="432bc-121">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="432bc-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="432bc-122">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="432bc-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="432bc-123">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="432bc-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="432bc-124">Windows Communication Foundation (WCF) 提供預設的對等驗證對受信任的人存放區的對等憑證的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="432bc-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="432bc-125">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="432bc-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="432bc-126">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="432bc-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="432bc-127">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="432bc-127">Optional enumeration.</span></span> <span data-ttu-id="432bc-128">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="432bc-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="432bc-129">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="432bc-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="432bc-130">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="432bc-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="432bc-131">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="432bc-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="432bc-132">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="432bc-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="432bc-133">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="432bc-133">Optional enumeration.</span></span> <span data-ttu-id="432bc-134">指定 WCF 安全性系統，驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="432bc-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="432bc-135">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="432bc-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="432bc-136">子元素</span><span class="sxs-lookup"><span data-stu-id="432bc-136">Child Elements</span></span>  
 <span data-ttu-id="432bc-137">無。</span><span class="sxs-lookup"><span data-stu-id="432bc-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="432bc-138">父項目</span><span class="sxs-lookup"><span data-stu-id="432bc-138">Parent Elements</span></span>  
  
|<span data-ttu-id="432bc-139">項目</span><span class="sxs-lookup"><span data-stu-id="432bc-139">Element</span></span>|<span data-ttu-id="432bc-140">描述</span><span class="sxs-lookup"><span data-stu-id="432bc-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="432bc-141">\<peer></span><span class="sxs-lookup"><span data-stu-id="432bc-141">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="432bc-142">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="432bc-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="432bc-143">備註</span><span class="sxs-lookup"><span data-stu-id="432bc-143">Remarks</span></span>  
 <span data-ttu-id="432bc-144">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="432bc-144">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="432bc-145">針對輸出通道，每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。</span><span class="sxs-lookup"><span data-stu-id="432bc-145">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="432bc-146">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="432bc-146">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="432bc-147">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="432bc-147">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432bc-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="432bc-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="432bc-149">使用憑證</span><span class="sxs-lookup"><span data-stu-id="432bc-149">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="432bc-150">對等網路</span><span class="sxs-lookup"><span data-stu-id="432bc-150">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="432bc-151">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="432bc-151">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="432bc-152">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="432bc-152">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="432bc-153">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="432bc-153">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
