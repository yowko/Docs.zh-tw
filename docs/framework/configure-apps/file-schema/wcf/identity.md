---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855148"
---
# <a name="identity"></a><span data-ttu-id="91a0a-101">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="91a0a-101">\<identity></span></span>
<span data-ttu-id="91a0a-102">身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="91a0a-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="91a0a-103">在用戶端和服務之間的交握程式中，Windows Communication Foundation （WCF）基礎結構將確保預期服務的身分識別符合此元素的值，因此可以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="91a0a-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="91a0a-104">如需詳細資訊，請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="91a0a-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="91a0a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91a0a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91a0a-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="91a0a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="91a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="91a0a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="91a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="91a0a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="91a0a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<身分識別 >**</span><span class="sxs-lookup"><span data-stu-id="91a0a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a0a-110">語法</span><span class="sxs-lookup"><span data-stu-id="91a0a-110">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91a0a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="91a0a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91a0a-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="91a0a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91a0a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="91a0a-113">Attributes</span></span>  
 <span data-ttu-id="91a0a-114">無。</span><span class="sxs-lookup"><span data-stu-id="91a0a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91a0a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="91a0a-115">Child Elements</span></span>  
  
|<span data-ttu-id="91a0a-116">項目</span><span class="sxs-lookup"><span data-stu-id="91a0a-116">Element</span></span>|<span data-ttu-id="91a0a-117">描述</span><span class="sxs-lookup"><span data-stu-id="91a0a-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91a0a-118">憑證 (certificate)</span><span class="sxs-lookup"><span data-stu-id="91a0a-118">certificate</span></span>|<span data-ttu-id="91a0a-119">指定 X.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="91a0a-119">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="91a0a-120">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。</span><span class="sxs-lookup"><span data-stu-id="91a0a-120">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="91a0a-121">它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。</span><span class="sxs-lookup"><span data-stu-id="91a0a-121">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="91a0a-122">certificateReference</span><span class="sxs-lookup"><span data-stu-id="91a0a-122">certificateReference</span></span>|<span data-ttu-id="91a0a-123">指定 X.509 憑證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="91a0a-123">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="91a0a-124">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。</span><span class="sxs-lookup"><span data-stu-id="91a0a-124">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="91a0a-125">dns</span><span class="sxs-lookup"><span data-stu-id="91a0a-125">dns</span></span>|<span data-ttu-id="91a0a-126">指定用來驗證服務之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="91a0a-126">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="91a0a-127">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="91a0a-127">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="91a0a-128">rsa</span><span class="sxs-lookup"><span data-stu-id="91a0a-128">rsa</span></span>|<span data-ttu-id="91a0a-129">指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。</span><span class="sxs-lookup"><span data-stu-id="91a0a-129">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="91a0a-130">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="91a0a-130">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="91a0a-131">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="91a0a-131">servicePrincipalName</span></span>|<span data-ttu-id="91a0a-132">指定伺服器主要名稱 (SPN) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="91a0a-132">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="91a0a-133">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="91a0a-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="91a0a-134">此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="91a0a-134">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="91a0a-135">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="91a0a-135">userPrincipalName</span></span>|<span data-ttu-id="91a0a-136">指定使用者主要名稱 (UPN) 身分識別，也就是網路上使用者的登入名稱類型。</span><span class="sxs-lookup"><span data-stu-id="91a0a-136">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="91a0a-137">使用者主體名稱包含 Active Directory 中使用的使用者物件名稱，後面接著 at 符號（\@），然後通常是網域名稱系統父系網域。</span><span class="sxs-lookup"><span data-stu-id="91a0a-137">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="91a0a-138">例如，Fabrikam.com 網域樹狀結構中的 Jeff 可能會有使用者主體名稱[jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)。</span><span class="sxs-lookup"><span data-stu-id="91a0a-138">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="91a0a-139">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="91a0a-139">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="91a0a-140">此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="91a0a-140">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91a0a-141">父項目</span><span class="sxs-lookup"><span data-stu-id="91a0a-141">Parent Elements</span></span>  
  
|<span data-ttu-id="91a0a-142">項目</span><span class="sxs-lookup"><span data-stu-id="91a0a-142">Element</span></span>|<span data-ttu-id="91a0a-143">說明</span><span class="sxs-lookup"><span data-stu-id="91a0a-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91a0a-144">\<custom></span><span class="sxs-lookup"><span data-stu-id="91a0a-144">\<custom></span></span>](custom.md)|<span data-ttu-id="91a0a-145">指定 netPeerTcpBinding 的自訂對等解析程式。</span><span class="sxs-lookup"><span data-stu-id="91a0a-145">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="91a0a-146">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="91a0a-146">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="91a0a-147">設定服務端點。</span><span class="sxs-lookup"><span data-stu-id="91a0a-147">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="91a0a-148">\<用戶端 > \<的端點 ></span><span class="sxs-lookup"><span data-stu-id="91a0a-148">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="91a0a-149">設定通道端點。</span><span class="sxs-lookup"><span data-stu-id="91a0a-149">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="91a0a-150">\<issuer></span><span class="sxs-lookup"><span data-stu-id="91a0a-150">\<issuer></span></span>](issuer.md)|<span data-ttu-id="91a0a-151">指定聯合服務的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="91a0a-151">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="91a0a-152">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="91a0a-152">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="91a0a-153">為聯合服務的安全性權杖服務 (STS) 指定中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="91a0a-153">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="91a0a-154">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="91a0a-154">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="91a0a-155">定義自訂繫結中已發行權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="91a0a-155">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="91a0a-156">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="91a0a-156">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="91a0a-157">指定本機安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="91a0a-157">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91a0a-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a0a-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="91a0a-159">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="91a0a-159">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="91a0a-160">終點位址、系結和合約</span><span class="sxs-lookup"><span data-stu-id="91a0a-160">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
