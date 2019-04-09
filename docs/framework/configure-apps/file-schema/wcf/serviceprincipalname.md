---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 75e95bcbaee229f19bdfdd119b548ed612f4ddaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204402"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="04a35-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="04a35-101">\<servicePrincipalName></span></span>
<span data-ttu-id="04a35-102">由其服務原則名稱 (SPN) 指定的服務身分識別。</span><span class="sxs-lookup"><span data-stu-id="04a35-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="04a35-103">如需有關如何設定 SPN 的詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="04a35-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="04a35-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="04a35-104">\<identity></span></span>  
<span data-ttu-id="04a35-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="04a35-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a35-106">語法</span><span class="sxs-lookup"><span data-stu-id="04a35-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04a35-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="04a35-107">Attributes and Elements</span></span>  
 <span data-ttu-id="04a35-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="04a35-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04a35-109">屬性</span><span class="sxs-lookup"><span data-stu-id="04a35-109">Attributes</span></span>  
  
|<span data-ttu-id="04a35-110">屬性</span><span class="sxs-lookup"><span data-stu-id="04a35-110">Attribute</span></span>|<span data-ttu-id="04a35-111">描述</span><span class="sxs-lookup"><span data-stu-id="04a35-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04a35-112">value</span><span class="sxs-lookup"><span data-stu-id="04a35-112">value</span></span>|<span data-ttu-id="04a35-113">用戶端用來唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="04a35-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="04a35-114">若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。</span><span class="sxs-lookup"><span data-stu-id="04a35-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="04a35-115">若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。</span><span class="sxs-lookup"><span data-stu-id="04a35-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04a35-116">子元素</span><span class="sxs-lookup"><span data-stu-id="04a35-116">Child Elements</span></span>  
 <span data-ttu-id="04a35-117">無。</span><span class="sxs-lookup"><span data-stu-id="04a35-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04a35-118">父項目</span><span class="sxs-lookup"><span data-stu-id="04a35-118">Parent Elements</span></span>  
  
|<span data-ttu-id="04a35-119">項目</span><span class="sxs-lookup"><span data-stu-id="04a35-119">Element</span></span>|<span data-ttu-id="04a35-120">描述</span><span class="sxs-lookup"><span data-stu-id="04a35-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04a35-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="04a35-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="04a35-122">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="04a35-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a35-123">備註</span><span class="sxs-lookup"><span data-stu-id="04a35-123">Remarks</span></span>  
 <span data-ttu-id="04a35-124">安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點對端點進行 SSPI 驗證時，會使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="04a35-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a35-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a35-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="04a35-126">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="04a35-126">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="04a35-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="04a35-127">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
