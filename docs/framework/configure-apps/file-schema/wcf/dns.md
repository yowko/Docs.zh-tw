---
title: '&lt;dns&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 2f5b9d5e1bc57230adbb32664e9ae15d3c71d46f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732611"
---
# <a name="ltdnsgt"></a><span data-ttu-id="2b14e-102">&lt;dns&gt;</span><span class="sxs-lookup"><span data-stu-id="2b14e-102">&lt;dns&gt;</span></span>
<span data-ttu-id="2b14e-103">指定伺服器的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="2b14e-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="2b14e-104">如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。</span><span class="sxs-lookup"><span data-stu-id="2b14e-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="2b14e-105">如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。</span><span class="sxs-lookup"><span data-stu-id="2b14e-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="2b14e-106">如需設定項目值的詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="2b14e-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="2b14e-107">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b14e-107">\<identity></span></span>  
<span data-ttu-id="2b14e-108">\<dns ></span><span class="sxs-lookup"><span data-stu-id="2b14e-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b14e-109">語法</span><span class="sxs-lookup"><span data-stu-id="2b14e-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b14e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2b14e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b14e-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2b14e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b14e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2b14e-112">Attributes</span></span>  
  
|<span data-ttu-id="2b14e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2b14e-113">Attribute</span></span>|<span data-ttu-id="2b14e-114">描述</span><span class="sxs-lookup"><span data-stu-id="2b14e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b14e-115">value</span><span class="sxs-lookup"><span data-stu-id="2b14e-115">value</span></span>|<span data-ttu-id="2b14e-116">憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="2b14e-116">The DNS of the certificate.</span></span> <span data-ttu-id="2b14e-117">DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="2b14e-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="2b14e-118">使用者可以記住顯示名稱，例如[ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929)或是[ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165)、 數字為基礎的位址，例如 207.46.131.137 比更容易。</span><span class="sxs-lookup"><span data-stu-id="2b14e-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b14e-119">子項目</span><span class="sxs-lookup"><span data-stu-id="2b14e-119">Child Elements</span></span>  
 <span data-ttu-id="2b14e-120">無。</span><span class="sxs-lookup"><span data-stu-id="2b14e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b14e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2b14e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2b14e-122">項目</span><span class="sxs-lookup"><span data-stu-id="2b14e-122">Element</span></span>|<span data-ttu-id="2b14e-123">描述</span><span class="sxs-lookup"><span data-stu-id="2b14e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b14e-124">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b14e-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2b14e-125">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="2b14e-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b14e-126">範例</span><span class="sxs-lookup"><span data-stu-id="2b14e-126">Example</span></span>  
 <span data-ttu-id="2b14e-127">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="2b14e-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b14e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b14e-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="2b14e-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="2b14e-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2b14e-130">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2b14e-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
