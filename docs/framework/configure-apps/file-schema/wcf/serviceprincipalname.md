---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 5d65b5956491e30066ece54a48374f1d7014552e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657573"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="869d9-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="869d9-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="869d9-103">由其服務原則名稱 (SPN) 指定的服務身分識別。</span><span class="sxs-lookup"><span data-stu-id="869d9-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="869d9-104">如需有關如何設定 SPN 的詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="869d9-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="869d9-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="869d9-105">\<identity></span></span>  
<span data-ttu-id="869d9-106">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="869d9-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="869d9-107">語法</span><span class="sxs-lookup"><span data-stu-id="869d9-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="869d9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="869d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="869d9-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="869d9-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="869d9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="869d9-110">Attributes</span></span>  
  
|<span data-ttu-id="869d9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="869d9-111">Attribute</span></span>|<span data-ttu-id="869d9-112">描述</span><span class="sxs-lookup"><span data-stu-id="869d9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="869d9-113">value</span><span class="sxs-lookup"><span data-stu-id="869d9-113">value</span></span>|<span data-ttu-id="869d9-114">用戶端用來唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="869d9-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="869d9-115">若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。</span><span class="sxs-lookup"><span data-stu-id="869d9-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="869d9-116">若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。</span><span class="sxs-lookup"><span data-stu-id="869d9-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="869d9-117">子元素</span><span class="sxs-lookup"><span data-stu-id="869d9-117">Child Elements</span></span>  
 <span data-ttu-id="869d9-118">無。</span><span class="sxs-lookup"><span data-stu-id="869d9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="869d9-119">父項目</span><span class="sxs-lookup"><span data-stu-id="869d9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="869d9-120">項目</span><span class="sxs-lookup"><span data-stu-id="869d9-120">Element</span></span>|<span data-ttu-id="869d9-121">描述</span><span class="sxs-lookup"><span data-stu-id="869d9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="869d9-122">\<identity></span><span class="sxs-lookup"><span data-stu-id="869d9-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="869d9-123">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="869d9-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="869d9-124">備註</span><span class="sxs-lookup"><span data-stu-id="869d9-124">Remarks</span></span>  
 <span data-ttu-id="869d9-125">安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點對端點進行 SSPI 驗證時，會使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="869d9-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869d9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="869d9-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="869d9-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="869d9-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="869d9-128">\<identity></span><span class="sxs-lookup"><span data-stu-id="869d9-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
