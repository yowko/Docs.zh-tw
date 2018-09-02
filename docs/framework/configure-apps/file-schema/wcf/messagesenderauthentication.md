---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 8a3beb42d1064e6c6629014369628248b4cd5c8d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416010"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="c4188-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="c4188-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="c4188-103">為訊息寄件者使用的對等憑證指定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="c4188-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="c4188-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4188-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4188-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c4188-105">\<behaviors></span></span>  
<span data-ttu-id="c4188-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4188-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c4188-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c4188-107">\<behavior></span></span>  
<span data-ttu-id="c4188-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c4188-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c4188-109">\<對等電腦 ></span><span class="sxs-lookup"><span data-stu-id="c4188-109">\<peer></span></span>  
<span data-ttu-id="c4188-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="c4188-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4188-111">語法</span><span class="sxs-lookup"><span data-stu-id="c4188-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4188-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4188-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c4188-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c4188-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4188-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c4188-114">Attributes</span></span>  
  
|<span data-ttu-id="c4188-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c4188-115">Attribute</span></span>|<span data-ttu-id="c4188-116">描述</span><span class="sxs-lookup"><span data-stu-id="c4188-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c4188-117">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="c4188-117">Optional enumeration.</span></span> <span data-ttu-id="c4188-118">指定用來驗證認證的五個模式之一。</span><span class="sxs-lookup"><span data-stu-id="c4188-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="c4188-119">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="c4188-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c4188-120">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="c4188-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c4188-121">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="c4188-121">Optional string.</span></span> <span data-ttu-id="c4188-122">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="c4188-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c4188-123">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="c4188-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c4188-124">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="c4188-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c4188-125">Windows Communication Foundation (WCF) 提供預設的對等驗證對受信任的人存放區的對等憑證的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="c4188-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c4188-126">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="c4188-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c4188-127">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="c4188-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c4188-128">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="c4188-128">Optional enumeration.</span></span> <span data-ttu-id="c4188-129">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="c4188-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c4188-130">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="c4188-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c4188-131">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="c4188-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c4188-132">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="c4188-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c4188-133">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="c4188-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c4188-134">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="c4188-134">Optional enumeration.</span></span> <span data-ttu-id="c4188-135">指定 WCF 安全性系統，驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="c4188-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="c4188-136">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="c4188-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4188-137">子元素</span><span class="sxs-lookup"><span data-stu-id="c4188-137">Child Elements</span></span>  
 <span data-ttu-id="c4188-138">無。</span><span class="sxs-lookup"><span data-stu-id="c4188-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4188-139">父項目</span><span class="sxs-lookup"><span data-stu-id="c4188-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c4188-140">項目</span><span class="sxs-lookup"><span data-stu-id="c4188-140">Element</span></span>|<span data-ttu-id="c4188-141">描述</span><span class="sxs-lookup"><span data-stu-id="c4188-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4188-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="c4188-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c4188-143">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="c4188-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4188-144">備註</span><span class="sxs-lookup"><span data-stu-id="c4188-144">Remarks</span></span>  
 <span data-ttu-id="c4188-145">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="c4188-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="c4188-146">針對輸出通道，每個訊息會使用簽章所提供的憑證[\<憑證 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)。</span><span class="sxs-lookup"><span data-stu-id="c4188-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="c4188-147">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="c4188-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="c4188-148">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="c4188-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4188-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4188-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="c4188-150">使用憑證</span><span class="sxs-lookup"><span data-stu-id="c4188-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c4188-151">對等網路</span><span class="sxs-lookup"><span data-stu-id="c4188-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="c4188-152">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="c4188-152">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="c4188-153">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="c4188-153">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="c4188-154">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="c4188-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
