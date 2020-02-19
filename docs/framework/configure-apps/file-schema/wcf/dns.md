---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452223"
---
# <a name="dns"></a><span data-ttu-id="e0d29-101">\<dns ></span><span class="sxs-lookup"><span data-stu-id="e0d29-101">\<dns></span></span>
<span data-ttu-id="e0d29-102">指定伺服器的預期身分識別。</span><span class="sxs-lookup"><span data-stu-id="e0d29-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e0d29-103">如果伺服器的憑證包含具有相同值的 DNS，這個身分識別對於 X509 憑證驗證模式是有效的。</span><span class="sxs-lookup"><span data-stu-id="e0d29-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e0d29-104">如果 SPN 具有相同的值，則對於 Windows 驗證模式也是有效的。</span><span class="sxs-lookup"><span data-stu-id="e0d29-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="e0d29-105">如需設定元素值的詳細資訊，請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="e0d29-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="e0d29-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e0d29-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e0d29-107">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e0d29-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e0d29-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="e0d29-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="e0d29-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="e0d29-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="e0d29-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identity >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="e0d29-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="e0d29-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**dns >**</span><span class="sxs-lookup"><span data-stu-id="e0d29-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0d29-112">語法</span><span class="sxs-lookup"><span data-stu-id="e0d29-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0d29-113">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e0d29-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e0d29-114">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e0d29-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0d29-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e0d29-115">Attributes</span></span>  
  
|<span data-ttu-id="e0d29-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e0d29-116">Attribute</span></span>|<span data-ttu-id="e0d29-117">描述</span><span class="sxs-lookup"><span data-stu-id="e0d29-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0d29-118">value</span><span class="sxs-lookup"><span data-stu-id="e0d29-118">value</span></span>|<span data-ttu-id="e0d29-119">憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="e0d29-119">The DNS of the certificate.</span></span> <span data-ttu-id="e0d29-120">DNS 是業界標準通訊協定，用來尋找 IP 網路上的電腦。</span><span class="sxs-lookup"><span data-stu-id="e0d29-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e0d29-121">使用者可以記住顯示名稱，例如 `https://go.microsoft.com/fwlink/?prd=10929` 或 `https://go.microsoft.com/fwlink/?LinkID=96165`，比以數位為基礎的位址（例如 207.46.131.137) 簡單）更容易。</span><span class="sxs-lookup"><span data-stu-id="e0d29-121">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0d29-122">子元素</span><span class="sxs-lookup"><span data-stu-id="e0d29-122">Child Elements</span></span>  
 <span data-ttu-id="e0d29-123">無。</span><span class="sxs-lookup"><span data-stu-id="e0d29-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0d29-124">父項目</span><span class="sxs-lookup"><span data-stu-id="e0d29-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e0d29-125">元素</span><span class="sxs-lookup"><span data-stu-id="e0d29-125">Element</span></span>|<span data-ttu-id="e0d29-126">描述</span><span class="sxs-lookup"><span data-stu-id="e0d29-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0d29-127">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="e0d29-127">\<identity></span></span>](identity.md)|<span data-ttu-id="e0d29-128">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="e0d29-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e0d29-129">範例</span><span class="sxs-lookup"><span data-stu-id="e0d29-129">Example</span></span>  
 <span data-ttu-id="e0d29-130">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的 DNS。</span><span class="sxs-lookup"><span data-stu-id="e0d29-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e0d29-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0d29-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e0d29-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="e0d29-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e0d29-133">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="e0d29-133">\<identity></span></span>](identity.md)
