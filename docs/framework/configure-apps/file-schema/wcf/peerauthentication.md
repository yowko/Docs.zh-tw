---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: a88a3c0bbbd36d2372520f70b3c5692757b35ade
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181553"
---
# \<peerAuthentication>

<span data-ttu-id="fd4bd-101">指定等節點使用之對等憑證的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="fd4bd-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd4bd-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd4bd-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd4bd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="fd4bd-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd4bd-105">屬性</span><span class="sxs-lookup"><span data-stu-id="fd4bd-105">Attributes</span></span>  
  
|<span data-ttu-id="fd4bd-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fd4bd-106">Attribute</span></span>|<span data-ttu-id="fd4bd-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd4bd-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="fd4bd-108">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-108">Optional enumeration.</span></span> <span data-ttu-id="fd4bd-109">指定用來驗證認證之三個模式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="fd4bd-110">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="fd4bd-111">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="fd4bd-112">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-112">Optional string.</span></span> <span data-ttu-id="fd4bd-113">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fd4bd-114">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="fd4bd-115">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="fd4bd-116">Windows Communication Foundation (WCF) 會提供預設的對等憑證驗證程式，以根據受信任的人存放區驗證對等憑證。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="fd4bd-117">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="fd4bd-118">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="fd4bd-119">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-119">Optional enumeration.</span></span> <span data-ttu-id="fd4bd-120">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="fd4bd-121">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="fd4bd-122">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="fd4bd-123">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="fd4bd-124">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fd4bd-125">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-125">Optional enumeration.</span></span> <span data-ttu-id="fd4bd-126">指定由 WCF 安全性系統驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="fd4bd-127">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd4bd-128">子元素</span><span class="sxs-lookup"><span data-stu-id="fd4bd-128">Child Elements</span></span>  

 <span data-ttu-id="fd4bd-129">無。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd4bd-130">父項目</span><span class="sxs-lookup"><span data-stu-id="fd4bd-130">Parent Elements</span></span>  
  
|<span data-ttu-id="fd4bd-131">項目</span><span class="sxs-lookup"><span data-stu-id="fd4bd-131">Element</span></span>|<span data-ttu-id="fd4bd-132">描述</span><span class="sxs-lookup"><span data-stu-id="fd4bd-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="fd4bd-133">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd4bd-134">備註</span><span class="sxs-lookup"><span data-stu-id="fd4bd-134">Remarks</span></span>  

 <span data-ttu-id="fd4bd-135">`<authentication>` 項目對應至 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 類別。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="fd4bd-136">這個項目會指定驗證程式，當網狀結構中進行鄰居對鄰居驗證時，就會叫用此驗證程式。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="fd4bd-137">當新對等嘗試建立鄰居連線時，它會將自己的認證傳遞至對應的對等。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="fd4bd-138">會叫用回應程式的驗證器來驗證遠端方的認證。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="fd4bd-139">每次在網狀結構中建立對等連線時，對等的兩方會互相驗證，亦即會叫用兩端的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="fd4bd-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4bd-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd4bd-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="fd4bd-141">使用憑證</span><span class="sxs-lookup"><span data-stu-id="fd4bd-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fd4bd-142">對等網路</span><span class="sxs-lookup"><span data-stu-id="fd4bd-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="fd4bd-143">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fd4bd-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="fd4bd-144">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fd4bd-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="fd4bd-145">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="fd4bd-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
