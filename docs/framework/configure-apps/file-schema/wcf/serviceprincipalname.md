---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f9b4ec506097cf010af78b3504def08102e0774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="23b41-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="23b41-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="23b41-103">由其服務原則名稱 (SPN) 指定的服務身分識別。</span><span class="sxs-lookup"><span data-stu-id="23b41-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="23b41-104">如需有關如何設定 SPN 的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="23b41-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="23b41-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="23b41-105">\<identity></span></span>  
<span data-ttu-id="23b41-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="23b41-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b41-107">語法</span><span class="sxs-lookup"><span data-stu-id="23b41-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23b41-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="23b41-108">Attributes and Elements</span></span>  
 <span data-ttu-id="23b41-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="23b41-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23b41-110">屬性</span><span class="sxs-lookup"><span data-stu-id="23b41-110">Attributes</span></span>  
  
|<span data-ttu-id="23b41-111">屬性</span><span class="sxs-lookup"><span data-stu-id="23b41-111">Attribute</span></span>|<span data-ttu-id="23b41-112">描述</span><span class="sxs-lookup"><span data-stu-id="23b41-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23b41-113">value</span><span class="sxs-lookup"><span data-stu-id="23b41-113">value</span></span>|<span data-ttu-id="23b41-114">用戶端用來唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="23b41-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="23b41-115">若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。</span><span class="sxs-lookup"><span data-stu-id="23b41-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="23b41-116">若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。</span><span class="sxs-lookup"><span data-stu-id="23b41-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23b41-117">子元素</span><span class="sxs-lookup"><span data-stu-id="23b41-117">Child Elements</span></span>  
 <span data-ttu-id="23b41-118">無。</span><span class="sxs-lookup"><span data-stu-id="23b41-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23b41-119">父項目</span><span class="sxs-lookup"><span data-stu-id="23b41-119">Parent Elements</span></span>  
  
|<span data-ttu-id="23b41-120">項目</span><span class="sxs-lookup"><span data-stu-id="23b41-120">Element</span></span>|<span data-ttu-id="23b41-121">描述</span><span class="sxs-lookup"><span data-stu-id="23b41-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23b41-122">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="23b41-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="23b41-123">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="23b41-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b41-124">備註</span><span class="sxs-lookup"><span data-stu-id="23b41-124">Remarks</span></span>  
 <span data-ttu-id="23b41-125">使用這個身分識別連接至端點的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端會在對端點進行 SSPI 驗證時使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="23b41-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b41-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="23b41-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="23b41-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="23b41-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="23b41-128">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="23b41-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
