---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: adfd94365ceb0ddc3164a6baef838c16027b4bc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190134"
---
# \<dns>

<span data-ttu-id="62a79-101">指定伺服器的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="62a79-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="62a79-102">如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。</span><span class="sxs-lookup"><span data-stu-id="62a79-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="62a79-103">如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。</span><span class="sxs-lookup"><span data-stu-id="62a79-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="62a79-104">如需設定元素值的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="62a79-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="62a79-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="62a79-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62a79-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62a79-106">Attributes and Elements</span></span>  

 <span data-ttu-id="62a79-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="62a79-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62a79-108">屬性</span><span class="sxs-lookup"><span data-stu-id="62a79-108">Attributes</span></span>  
  
|<span data-ttu-id="62a79-109">屬性</span><span class="sxs-lookup"><span data-stu-id="62a79-109">Attribute</span></span>|<span data-ttu-id="62a79-110">描述</span><span class="sxs-lookup"><span data-stu-id="62a79-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62a79-111">value</span><span class="sxs-lookup"><span data-stu-id="62a79-111">value</span></span>|<span data-ttu-id="62a79-112">憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="62a79-112">The DNS of the certificate.</span></span> <span data-ttu-id="62a79-113">DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="62a79-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="62a79-114">使用者可以記住顯示名稱，例如 `https://go.microsoft.com/fwlink/?prd=10929` 或 `https://go.microsoft.com/fwlink/?LinkID=96165` ，比以數位為基礎的位址（例如 207.46.131.137) 簡單）更容易。</span><span class="sxs-lookup"><span data-stu-id="62a79-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62a79-115">子元素</span><span class="sxs-lookup"><span data-stu-id="62a79-115">Child Elements</span></span>  

 <span data-ttu-id="62a79-116">無。</span><span class="sxs-lookup"><span data-stu-id="62a79-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62a79-117">父項目</span><span class="sxs-lookup"><span data-stu-id="62a79-117">Parent Elements</span></span>  
  
|<span data-ttu-id="62a79-118">項目</span><span class="sxs-lookup"><span data-stu-id="62a79-118">Element</span></span>|<span data-ttu-id="62a79-119">描述</span><span class="sxs-lookup"><span data-stu-id="62a79-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="62a79-120">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="62a79-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62a79-121">範例</span><span class="sxs-lookup"><span data-stu-id="62a79-121">Example</span></span>  

 <span data-ttu-id="62a79-122">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="62a79-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="62a79-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62a79-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="62a79-124">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="62a79-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
