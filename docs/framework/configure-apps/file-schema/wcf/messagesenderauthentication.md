---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 035f3c95fc876f0d451e6b2146e754cfe0959a85
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546981"
---
# \<messageSenderAuthentication>
<span data-ttu-id="71399-101">為訊息寄件者使用的對等憑證指定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="71399-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="71399-102">語法</span><span class="sxs-lookup"><span data-stu-id="71399-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71399-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="71399-103">Attributes and Elements</span></span>  
 <span data-ttu-id="71399-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="71399-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71399-105">屬性</span><span class="sxs-lookup"><span data-stu-id="71399-105">Attributes</span></span>  
  
|<span data-ttu-id="71399-106">屬性</span><span class="sxs-lookup"><span data-stu-id="71399-106">Attribute</span></span>|<span data-ttu-id="71399-107">描述</span><span class="sxs-lookup"><span data-stu-id="71399-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="71399-108">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="71399-108">Optional enumeration.</span></span> <span data-ttu-id="71399-109">指定用來驗證認證的五個模式之一。</span><span class="sxs-lookup"><span data-stu-id="71399-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="71399-110">此屬性的型別為 <xref:System.ServiceModel.Security.X509CertificateValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="71399-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="71399-111">如果設定為 `Custom`，也必須提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="71399-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="71399-112">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="71399-112">Optional string.</span></span> <span data-ttu-id="71399-113">指定用來驗證自訂型別的型別和組件。</span><span class="sxs-lookup"><span data-stu-id="71399-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="71399-114">當 `certificateValidationMode` 設定為 `Custom` 時，必須設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="71399-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="71399-115">此屬性的型別為 <xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="71399-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="71399-116">Windows Communication Foundation (WCF) 會提供預設的對等憑證驗證程式，以根據受信任的人存放區驗證對等憑證。</span><span class="sxs-lookup"><span data-stu-id="71399-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="71399-117">它也會驗證憑證鏈結直到有效根憑證。</span><span class="sxs-lookup"><span data-stu-id="71399-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="71399-118">您可以實作自訂的驗證程式以指定不同的行為，並使用這個屬性指向自訂的驗證程式。</span><span class="sxs-lookup"><span data-stu-id="71399-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="71399-119">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="71399-119">Optional enumeration.</span></span> <span data-ttu-id="71399-120">指定憑證撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="71399-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="71399-121">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="71399-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="71399-122">系統會在撤銷憑證清單中查詢，以確認對等憑證尚未被撤銷。</span><span class="sxs-lookup"><span data-stu-id="71399-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="71399-123">這項檢查可以藉由線上檢查或是針對快取的撤銷清單來執行。</span><span class="sxs-lookup"><span data-stu-id="71399-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="71399-124">將此屬性設定為 NoCheck 可以關閉撤銷檢查。</span><span class="sxs-lookup"><span data-stu-id="71399-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="71399-125">選擇性列舉。</span><span class="sxs-lookup"><span data-stu-id="71399-125">Optional enumeration.</span></span> <span data-ttu-id="71399-126">指定由 WCF 安全性系統驗證對等憑證的受信任存放區位置。</span><span class="sxs-lookup"><span data-stu-id="71399-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="71399-127">此屬性的型別為 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="71399-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71399-128">子元素</span><span class="sxs-lookup"><span data-stu-id="71399-128">Child Elements</span></span>  
 <span data-ttu-id="71399-129">無。</span><span class="sxs-lookup"><span data-stu-id="71399-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71399-130">父項目</span><span class="sxs-lookup"><span data-stu-id="71399-130">Parent Elements</span></span>  
  
|<span data-ttu-id="71399-131">項目</span><span class="sxs-lookup"><span data-stu-id="71399-131">Element</span></span>|<span data-ttu-id="71399-132">描述</span><span class="sxs-lookup"><span data-stu-id="71399-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="71399-133">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="71399-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71399-134">備註</span><span class="sxs-lookup"><span data-stu-id="71399-134">Remarks</span></span>  
 <span data-ttu-id="71399-135">如果已選取訊息驗證，則必須設定這個項目。</span><span class="sxs-lookup"><span data-stu-id="71399-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="71399-136">針對輸出通道，每個訊息都會使用所提供的憑證進行簽署 [\<certificate>](certificate-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="71399-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="71399-137">所有訊息在傳遞至應用程式之前，都會使用這個項目的 `customCertificateValidatorType` 之屬性所指定的驗證程式來檢查訊息認證。</span><span class="sxs-lookup"><span data-stu-id="71399-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="71399-138">驗證器可接受或拒絕認證。</span><span class="sxs-lookup"><span data-stu-id="71399-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71399-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71399-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="71399-140">使用憑證</span><span class="sxs-lookup"><span data-stu-id="71399-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="71399-141">對等網路</span><span class="sxs-lookup"><span data-stu-id="71399-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="71399-142">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="71399-142">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="71399-143">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="71399-143">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="71399-144">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="71399-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
