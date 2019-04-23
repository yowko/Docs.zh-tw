---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 0f5eace346fd0ed2c0532fb602585c4593d97291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220353"
---
# <a name="identity"></a><span data-ttu-id="d0e41-101">\<identity></span><span class="sxs-lookup"><span data-stu-id="d0e41-101">\<identity></span></span>
<span data-ttu-id="d0e41-102">身分識別項目允許用戶端開發人員在設計階段指定服務的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="d0e41-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="d0e41-103">在用戶端與服務之間的信號交換過程中的 Windows Communication Foundation (WCF) 基礎結構可確保預期的服務符合這個元素的值的身分識別，且因此可進行驗證。</span><span class="sxs-lookup"><span data-stu-id="d0e41-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="d0e41-104">如需詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e41-104">For more information, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="d0e41-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0e41-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0e41-106">\<client></span><span class="sxs-lookup"><span data-stu-id="d0e41-106">\<client></span></span>  
<span data-ttu-id="d0e41-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d0e41-107">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0e41-108">語法</span><span class="sxs-lookup"><span data-stu-id="d0e41-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0e41-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d0e41-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d0e41-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d0e41-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0e41-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d0e41-111">Attributes</span></span>  
 <span data-ttu-id="d0e41-112">無。</span><span class="sxs-lookup"><span data-stu-id="d0e41-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d0e41-113">子元素</span><span class="sxs-lookup"><span data-stu-id="d0e41-113">Child Elements</span></span>  
  
|<span data-ttu-id="d0e41-114">項目</span><span class="sxs-lookup"><span data-stu-id="d0e41-114">Element</span></span>|<span data-ttu-id="d0e41-115">描述</span><span class="sxs-lookup"><span data-stu-id="d0e41-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0e41-116">憑證</span><span class="sxs-lookup"><span data-stu-id="d0e41-116">certificate</span></span>|<span data-ttu-id="d0e41-117">指定 X.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="d0e41-117">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="d0e41-118">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateElement>。</span><span class="sxs-lookup"><span data-stu-id="d0e41-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="d0e41-119">它包含是字串的屬性 `encodedValue`，指定由此憑證編碼的值。</span><span class="sxs-lookup"><span data-stu-id="d0e41-119">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="d0e41-120">certificateReference</span><span class="sxs-lookup"><span data-stu-id="d0e41-120">certificateReference</span></span>|<span data-ttu-id="d0e41-121">指定 X.509 憑證驗證的設定。</span><span class="sxs-lookup"><span data-stu-id="d0e41-121">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="d0e41-122">此項目的型別為 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>。</span><span class="sxs-lookup"><span data-stu-id="d0e41-122">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="d0e41-123">dns</span><span class="sxs-lookup"><span data-stu-id="d0e41-123">dns</span></span>|<span data-ttu-id="d0e41-124">指定用來驗證服務之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="d0e41-124">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="d0e41-125">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d0e41-125">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="d0e41-126">rsa</span><span class="sxs-lookup"><span data-stu-id="d0e41-126">rsa</span></span>|<span data-ttu-id="d0e41-127">指定 X.509 憑證的 RSA 欄位值，此憑證可用來驗證用戶端的服務。</span><span class="sxs-lookup"><span data-stu-id="d0e41-127">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="d0e41-128">這個項目包含是字串的屬性 `value`，而且包含實際的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d0e41-128">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="d0e41-129">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="d0e41-129">servicePrincipalName</span></span>|<span data-ttu-id="d0e41-130">指定伺服器主要名稱 (SPN) 身分識別，也就是用戶端可唯一識別服務執行個體時所用的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e41-130">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="d0e41-131">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e41-131">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="d0e41-132">此項目的型別為 <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="d0e41-132">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="d0e41-133">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="d0e41-133">userPrincipalName</span></span>|<span data-ttu-id="d0e41-134">指定使用者主要名稱 (UPN) 身分識別，也就是網路上使用者的登入名稱類型。</span><span class="sxs-lookup"><span data-stu-id="d0e41-134">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="d0e41-135">使用者主體名稱包含使用者物件名稱後面加上的 Active Directory 中使用 at 符號 (\@)，然後一般而言，網域名稱系統父系網域。</span><span class="sxs-lookup"><span data-stu-id="d0e41-135">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="d0e41-136">例如，Fabrikam.com 網域樹狀目錄中的 Jeff 可能會有使用者主體名稱[ jeff@fabrikam.com ](mailto:jeffsmith@fabrikam.com)。</span><span class="sxs-lookup"><span data-stu-id="d0e41-136">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="d0e41-137">這個項目包含是字串的屬性 `value`，而且包含實際的主要名稱。</span><span class="sxs-lookup"><span data-stu-id="d0e41-137">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="d0e41-138">此項目的型別為 <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>。</span><span class="sxs-lookup"><span data-stu-id="d0e41-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d0e41-139">父項目</span><span class="sxs-lookup"><span data-stu-id="d0e41-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d0e41-140">項目</span><span class="sxs-lookup"><span data-stu-id="d0e41-140">Element</span></span>|<span data-ttu-id="d0e41-141">描述</span><span class="sxs-lookup"><span data-stu-id="d0e41-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0e41-142">\<custom></span><span class="sxs-lookup"><span data-stu-id="d0e41-142">\<custom></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custom.md)|<span data-ttu-id="d0e41-143">指定 netPeerTcpBinding 的自訂對等解析程式。</span><span class="sxs-lookup"><span data-stu-id="d0e41-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="d0e41-144">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="d0e41-144">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="d0e41-145">設定服務端點。</span><span class="sxs-lookup"><span data-stu-id="d0e41-145">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="d0e41-146">\<端點 > 的\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="d0e41-146">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="d0e41-147">設定通道端點。</span><span class="sxs-lookup"><span data-stu-id="d0e41-147">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="d0e41-148">\<issuer></span><span class="sxs-lookup"><span data-stu-id="d0e41-148">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="d0e41-149">指定聯合服務的安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="d0e41-149">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="d0e41-150">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="d0e41-150">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="d0e41-151">為聯合服務的安全性權杖服務 (STS) 指定中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="d0e41-151">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="d0e41-152">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="d0e41-152">\<issuedTokenParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|<span data-ttu-id="d0e41-153">定義自訂繫結中已發行權杖的參數。</span><span class="sxs-lookup"><span data-stu-id="d0e41-153">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="d0e41-154">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="d0e41-154">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="d0e41-155">指定本機安全性權杖服務 (STS)。</span><span class="sxs-lookup"><span data-stu-id="d0e41-155">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0e41-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e41-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="d0e41-157">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d0e41-157">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d0e41-158">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="d0e41-158">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
