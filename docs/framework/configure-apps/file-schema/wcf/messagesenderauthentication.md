---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 4749aeebedd9f918c2ed1a119767681f4c3ded37
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263663"
---
# <a name="messagesenderauthentication"></a><span data-ttu-id="36e95-101">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="36e95-101">\<messageSenderAuthentication></span></span>
<span data-ttu-id="36e95-102">為訊息寄件者使用的對等憑證指定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="36e95-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="36e95-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="36e95-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="36e95-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="36e95-104">\<behaviors></span></span>  
<span data-ttu-id="36e95-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="36e95-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="36e95-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="36e95-106">\<behavior></span></span>  
<span data-ttu-id="36e95-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="36e95-107">\<serviceCredentials></span></span>  
<span data-ttu-id="36e95-108">\<peer></span><span class="sxs-lookup"><span data-stu-id="36e95-108">\<peer></span></span>  
<span data-ttu-id="36e95-109">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="36e95-109">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e95-110">語法</span><span class="sxs-lookup"><span data-stu-id="36e95-110">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36e95-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36e95-111">Attributes and Elements</span></span>  
 <span data-ttu-id="36e95-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="36e95-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36e95-113">屬性</span><span class="sxs-lookup"><span data-stu-id="36e95-113">Attributes</span></span>  
  
|<span data-ttu-id="36e95-114">屬性</span><span class="sxs-lookup"><span data-stu-id="36e95-114">Attribute</span></span>|<span data-ttu-id="36e95-115">描述</span><span class="sxs-lookup"><span data-stu-id="36e95-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="36e95-116">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="36e95-116">Optional enumeration.</span></span> <span data-ttu-id="36e95-117">指定用來驗證認證的五個模式之一。</span><span class="sxs-lookup"><span data-stu-id="36e95-117">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="36e95-118">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="36e95-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="36e95-119">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="36e95-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="36e95-120">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="36e95-120">Optional string.</span></span> <span data-ttu-id="36e95-121">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="36e95-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="36e95-122">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="36e95-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="36e95-123">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="36e95-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="36e95-124">Windows Communication Foundation (WCF) 提供預設的對等驗證對受信任的人存放區的對等憑證的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="36e95-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="36e95-125">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="36e95-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="36e95-126">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="36e95-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="36e95-127">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="36e95-127">Optional enumeration.</span></span> <span data-ttu-id="36e95-128">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="36e95-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="36e95-129">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="36e95-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="36e95-130">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="36e95-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="36e95-131">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="36e95-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="36e95-132">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="36e95-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="36e95-133">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="36e95-133">Optional enumeration.</span></span> <span data-ttu-id="36e95-134">指定 WCF 安全性系統，驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="36e95-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="36e95-135">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="36e95-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36e95-136">子元素</span><span class="sxs-lookup"><span data-stu-id="36e95-136">Child Elements</span></span>  
 <span data-ttu-id="36e95-137">無。</span><span class="sxs-lookup"><span data-stu-id="36e95-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36e95-138">父項目</span><span class="sxs-lookup"><span data-stu-id="36e95-138">Parent Elements</span></span>  
  
|<span data-ttu-id="36e95-139">項目</span><span class="sxs-lookup"><span data-stu-id="36e95-139">Element</span></span>|<span data-ttu-id="36e95-140">描述</span><span class="sxs-lookup"><span data-stu-id="36e95-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36e95-141">\<peer></span><span class="sxs-lookup"><span data-stu-id="36e95-141">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="36e95-142">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="36e95-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36e95-143">備註</span><span class="sxs-lookup"><span data-stu-id="36e95-143">Remarks</span></span>  
 <span data-ttu-id="36e95-144">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="36e95-144">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="36e95-145">針對輸出通道，每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。</span><span class="sxs-lookup"><span data-stu-id="36e95-145">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="36e95-146">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="36e95-146">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="36e95-147">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="36e95-147">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e95-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36e95-148">See also</span></span>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="36e95-149">使用憑證</span><span class="sxs-lookup"><span data-stu-id="36e95-149">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="36e95-150">對等網路</span><span class="sxs-lookup"><span data-stu-id="36e95-150">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="36e95-151">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="36e95-151">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="36e95-152">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="36e95-152">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="36e95-153">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="36e95-153">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
