---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919129"
---
# <a name="dns"></a><span data-ttu-id="51bfc-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="51bfc-101">\<dns></span></span>
<span data-ttu-id="51bfc-102">指定伺服器的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="51bfc-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="51bfc-103">如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。</span><span class="sxs-lookup"><span data-stu-id="51bfc-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="51bfc-104">如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。</span><span class="sxs-lookup"><span data-stu-id="51bfc-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="51bfc-105">如需設定元素值的詳細資訊, 請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="51bfc-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="51bfc-106">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="51bfc-106">\<identity></span></span>  
<span data-ttu-id="51bfc-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="51bfc-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51bfc-108">語法</span><span class="sxs-lookup"><span data-stu-id="51bfc-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51bfc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="51bfc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="51bfc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="51bfc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51bfc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="51bfc-111">Attributes</span></span>  
  
|<span data-ttu-id="51bfc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="51bfc-112">Attribute</span></span>|<span data-ttu-id="51bfc-113">描述</span><span class="sxs-lookup"><span data-stu-id="51bfc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51bfc-114">value</span><span class="sxs-lookup"><span data-stu-id="51bfc-114">value</span></span>|<span data-ttu-id="51bfc-115">憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="51bfc-115">The DNS of the certificate.</span></span> <span data-ttu-id="51bfc-116">DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="51bfc-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="51bfc-117">使用者可以記住顯示名稱, 例如<https://go.microsoft.com/fwlink/?prd=10929>或[https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), 比以數位為基礎的位址 (例如 207.46.131.137) 簡單) 更容易。</span><span class="sxs-lookup"><span data-stu-id="51bfc-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51bfc-118">子元素</span><span class="sxs-lookup"><span data-stu-id="51bfc-118">Child Elements</span></span>  
 <span data-ttu-id="51bfc-119">無。</span><span class="sxs-lookup"><span data-stu-id="51bfc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51bfc-120">父項目</span><span class="sxs-lookup"><span data-stu-id="51bfc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="51bfc-121">項目</span><span class="sxs-lookup"><span data-stu-id="51bfc-121">Element</span></span>|<span data-ttu-id="51bfc-122">說明</span><span class="sxs-lookup"><span data-stu-id="51bfc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51bfc-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="51bfc-123">\<identity></span></span>](identity.md)|<span data-ttu-id="51bfc-124">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="51bfc-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="51bfc-125">範例</span><span class="sxs-lookup"><span data-stu-id="51bfc-125">Example</span></span>  
 <span data-ttu-id="51bfc-126">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="51bfc-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="51bfc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51bfc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="51bfc-128">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="51bfc-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="51bfc-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="51bfc-129">\<identity></span></span>](identity.md)
