---
title: '&lt;Dns&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 6125bf157d04a1b0298a183465d11a18ac3786f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdnsgt"></a><span data-ttu-id="2b1f7-102">&lt;Dns&gt;</span><span class="sxs-lookup"><span data-stu-id="2b1f7-102">&lt;dns&gt;</span></span>
<span data-ttu-id="2b1f7-103">指定伺服器的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="2b1f7-104">如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="2b1f7-105">如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="2b1f7-106">如需有關設定項目值的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2b1f7-107">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b1f7-107">\<identity></span></span>  
<span data-ttu-id="2b1f7-108">\<dns ></span><span class="sxs-lookup"><span data-stu-id="2b1f7-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1f7-109">語法</span><span class="sxs-lookup"><span data-stu-id="2b1f7-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b1f7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b1f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b1f7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b1f7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2b1f7-112">Attributes</span></span>  
  
|<span data-ttu-id="2b1f7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2b1f7-113">Attribute</span></span>|<span data-ttu-id="2b1f7-114">描述</span><span class="sxs-lookup"><span data-stu-id="2b1f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b1f7-115">value</span><span class="sxs-lookup"><span data-stu-id="2b1f7-115">value</span></span>|<span data-ttu-id="2b1f7-116">憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-116">The DNS of the certificate.</span></span> <span data-ttu-id="2b1f7-117">DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="2b1f7-118">使用者可記住顯示名稱，例如[ http://go.microsoft.com/fwlink/?prd=10929 ](http://go.microsoft.com/fwlink/?prd=10929)或[ http://go.microsoft.com/fwlink/?LinkID=96165 ](http://go.microsoft.com/fwlink/?LinkID=96165)、 數字為基礎的位址，例如 207.46.131.137 比更容易。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b1f7-119">子項目</span><span class="sxs-lookup"><span data-stu-id="2b1f7-119">Child Elements</span></span>  
 <span data-ttu-id="2b1f7-120">無。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b1f7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2b1f7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b1f7-122">項目</span><span class="sxs-lookup"><span data-stu-id="2b1f7-122">Element</span></span>|<span data-ttu-id="2b1f7-123">描述</span><span class="sxs-lookup"><span data-stu-id="2b1f7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b1f7-124">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b1f7-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2b1f7-125">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b1f7-126">範例</span><span class="sxs-lookup"><span data-stu-id="2b1f7-126">Example</span></span>  
 <span data-ttu-id="2b1f7-127">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="2b1f7-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b1f7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b1f7-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="2b1f7-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="2b1f7-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2b1f7-130">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b1f7-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
