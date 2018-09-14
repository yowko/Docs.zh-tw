---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569134"
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="44e4e-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="44e4e-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="44e4e-103">指定等節點使用之對等憑證的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="44e4e-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="44e4e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44e4e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="44e4e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="44e4e-105">\<behaviors></span></span>  
<span data-ttu-id="44e4e-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="44e4e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="44e4e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="44e4e-107">\<behavior></span></span>  
<span data-ttu-id="44e4e-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="44e4e-108">\<serviceCredentials></span></span>  
<span data-ttu-id="44e4e-109">\<對等電腦 ></span><span class="sxs-lookup"><span data-stu-id="44e4e-109">\<peer></span></span>  
<span data-ttu-id="44e4e-110">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="44e4e-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e4e-111">語法</span><span class="sxs-lookup"><span data-stu-id="44e4e-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44e4e-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="44e4e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="44e4e-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="44e4e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44e4e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="44e4e-114">Attributes</span></span>  
  
|<span data-ttu-id="44e4e-115">屬性</span><span class="sxs-lookup"><span data-stu-id="44e4e-115">Attribute</span></span>|<span data-ttu-id="44e4e-116">描述</span><span class="sxs-lookup"><span data-stu-id="44e4e-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="44e4e-117">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="44e4e-117">Optional enumeration.</span></span> <span data-ttu-id="44e4e-118">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="44e4e-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="44e4e-119">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="44e4e-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="44e4e-120">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="44e4e-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="44e4e-121">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="44e4e-121">Optional string.</span></span> <span data-ttu-id="44e4e-122">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="44e4e-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="44e4e-123">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="44e4e-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="44e4e-124">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="44e4e-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="44e4e-125">Windows Communication Foundation (WCF) 提供預設的對等驗證對受信任的人存放區的對等憑證的憑證驗證程式。</span><span class="sxs-lookup"><span data-stu-id="44e4e-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="44e4e-126">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="44e4e-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="44e4e-127">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="44e4e-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="44e4e-128">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="44e4e-128">Optional enumeration.</span></span> <span data-ttu-id="44e4e-129">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="44e4e-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="44e4e-130">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="44e4e-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="44e4e-131">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="44e4e-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="44e4e-132">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="44e4e-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="44e4e-133">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="44e4e-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="44e4e-134">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="44e4e-134">Optional enumeration.</span></span> <span data-ttu-id="44e4e-135">指定 WCF 安全性系統，驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="44e4e-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="44e4e-136">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="44e4e-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44e4e-137">子元素</span><span class="sxs-lookup"><span data-stu-id="44e4e-137">Child Elements</span></span>  
 <span data-ttu-id="44e4e-138">無。</span><span class="sxs-lookup"><span data-stu-id="44e4e-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44e4e-139">父項目</span><span class="sxs-lookup"><span data-stu-id="44e4e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="44e4e-140">項目</span><span class="sxs-lookup"><span data-stu-id="44e4e-140">Element</span></span>|<span data-ttu-id="44e4e-141">描述</span><span class="sxs-lookup"><span data-stu-id="44e4e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44e4e-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="44e4e-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="44e4e-143">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="44e4e-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e4e-144">備註</span><span class="sxs-lookup"><span data-stu-id="44e4e-144">Remarks</span></span>  
 <span data-ttu-id="44e4e-145">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="44e4e-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="44e4e-146">這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。</span><span class="sxs-lookup"><span data-stu-id="44e4e-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="44e4e-147">當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。</span><span class="sxs-lookup"><span data-stu-id="44e4e-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="44e4e-148">會叫用回應程式的驗證器來驗證遠端方的認證。</span><span class="sxs-lookup"><span data-stu-id="44e4e-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="44e4e-149">每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="44e4e-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e4e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44e4e-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="44e4e-151">使用憑證</span><span class="sxs-lookup"><span data-stu-id="44e4e-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="44e4e-152">對等網路</span><span class="sxs-lookup"><span data-stu-id="44e4e-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="44e4e-153">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="44e4e-153">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="44e4e-154">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="44e4e-154">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="44e4e-155">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="44e4e-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
