---
title: '&lt;identity&gt;'
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 8d4074319a10abc1ce4aafe15e3b51381398c39c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146507"
---
# <a name="ltidentitygt"></a><span data-ttu-id="6b717-102">&lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="6b717-102">&lt;identity&gt;</span></span>
<span data-ttu-id="6b717-103">身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="6b717-103">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="6b717-104">在用戶端與服務之間的信號交換過程中的 Windows Communication Foundation (WCF) 基礎結構可確保預期的服務符合這個元素的值的身分識別，且因此可進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6b717-104">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="6b717-105">如需詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="6b717-105">For more information, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="6b717-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b717-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b717-107">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="6b717-107">\<client></span></span>  
<span data-ttu-id="6b717-108">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="6b717-108">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b717-109">語法</span><span class="sxs-lookup"><span data-stu-id="6b717-109">Syntax</span></span>  
  
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
  <usePrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b717-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6b717-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b717-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6b717-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b717-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6b717-112">Attributes</span></span>  
 <span data-ttu-id="6b717-113">無。</span><span class="sxs-lookup"><span data-stu-id="6b717-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b717-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6b717-114">Child Elements</span></span>  
  
|<span data-ttu-id="6b717-115">項目</span><span class="sxs-lookup"><span data-stu-id="6b717-115">Element</span></span>|<span data-ttu-id="6b717-116">描述</span><span class="sxs-lookup"><span data-stu-id="6b717-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b717-117">certificate</span><span class="sxs-lookup"><span data-stu-id="6b717-117">certificate</span></span>|<span data-ttu-id="6b717-118">指定 X.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="6b717-118">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="6b717-119">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。</span><span class="sxs-lookup"><span data-stu-id="6b717-119">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="6b717-120">它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。</span><span class="sxs-lookup"><span data-stu-id="6b717-120">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="6b717-121">certificateReference</span><span class="sxs-lookup"><span data-stu-id="6b717-121">certificateReference</span></span>|<span data-ttu-id="6b717-122">指定 X.509 憑證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="6b717-122">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="6b717-123">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。</span><span class="sxs-lookup"><span data-stu-id="6b717-123">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="6b717-124">dns</span><span class="sxs-lookup"><span data-stu-id="6b717-124">dns</span></span>|<span data-ttu-id="6b717-125">指定用來驗證服務之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="6b717-125">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="6b717-126">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="6b717-126">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="6b717-127">rsa</span><span class="sxs-lookup"><span data-stu-id="6b717-127">rsa</span></span>|<span data-ttu-id="6b717-128">指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。</span><span class="sxs-lookup"><span data-stu-id="6b717-128">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="6b717-129">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="6b717-129">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="6b717-130">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="6b717-130">servicePrincipalName</span></span>|<span data-ttu-id="6b717-131">指定伺服器主要名稱 (SPN) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="6b717-131">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="6b717-132">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="6b717-132">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="6b717-133">此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="6b717-133">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="6b717-134">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="6b717-134">userPrincipalName</span></span>|<span data-ttu-id="6b717-135">指定使用者主要名稱 (UPN) 身分識別，也就是網路上使用者的登入名稱類型。</span><span class="sxs-lookup"><span data-stu-id="6b717-135">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="6b717-136">使用者主體名稱包含使用者物件名稱後面加上的 Active Directory 中使用 at 符號 (\@)，然後一般而言，網域名稱系統父系網域。</span><span class="sxs-lookup"><span data-stu-id="6b717-136">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="6b717-137">例如，Fabrikam.com 網域樹狀目錄中的 Jeff 可能會有使用者主體名稱[ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com)。</span><span class="sxs-lookup"><span data-stu-id="6b717-137">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="6b717-138">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="6b717-138">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="6b717-139">此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="6b717-139">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b717-140">父項目</span><span class="sxs-lookup"><span data-stu-id="6b717-140">Parent Elements</span></span>  
  
|<span data-ttu-id="6b717-141">項目</span><span class="sxs-lookup"><span data-stu-id="6b717-141">Element</span></span>|<span data-ttu-id="6b717-142">描述</span><span class="sxs-lookup"><span data-stu-id="6b717-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b717-143">\<custom></span><span class="sxs-lookup"><span data-stu-id="6b717-143">\<custom></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|<span data-ttu-id="6b717-144">指定 netPeerTcpBinding 的自訂對等解析程式。</span><span class="sxs-lookup"><span data-stu-id="6b717-144">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="6b717-145">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="6b717-145">\<endpoint></span></span>](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)|<span data-ttu-id="6b717-146">設定不同類型的端點。</span><span class="sxs-lookup"><span data-stu-id="6b717-146">Configures different types of endpoints.</span></span>|  
|[<span data-ttu-id="6b717-147">\<issuer></span><span class="sxs-lookup"><span data-stu-id="6b717-147">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="6b717-148">指定聯合服務的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="6b717-148">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="6b717-149">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="6b717-149">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="6b717-150">為聯合服務的安全性權杖服務 (STS) 指定中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="6b717-150">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="6b717-151">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="6b717-151">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="6b717-152">定義自訂繫結中已發行權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="6b717-152">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="6b717-153">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="6b717-153">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="6b717-154">指定本機安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="6b717-154">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b717-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b717-155">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 [<span data-ttu-id="6b717-156">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="6b717-156">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="6b717-157">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="6b717-157">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
