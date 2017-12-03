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
ms.openlocfilehash: b734a095f0c9ea9ad1bd6e78f3ef4264f4f2317e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="7eeeb-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="7eeeb-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="7eeeb-103">由其服務原則名稱 (SPN) 指定的服務身分識別。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="7eeeb-104">如需有關如何設定 SPN 的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7eeeb-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="7eeeb-105">\<identity></span></span>  
<span data-ttu-id="7eeeb-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="7eeeb-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eeeb-107">語法</span><span class="sxs-lookup"><span data-stu-id="7eeeb-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7eeeb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7eeeb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7eeeb-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="7eeeb-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7eeeb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7eeeb-110">Attributes</span></span>  
  
|<span data-ttu-id="7eeeb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7eeeb-111">Attribute</span></span>|<span data-ttu-id="7eeeb-112">描述</span><span class="sxs-lookup"><span data-stu-id="7eeeb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7eeeb-113">value</span><span class="sxs-lookup"><span data-stu-id="7eeeb-113">value</span></span>|<span data-ttu-id="7eeeb-114">用戶端用來唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="7eeeb-115">若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="7eeeb-116">若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7eeeb-117">子元素</span><span class="sxs-lookup"><span data-stu-id="7eeeb-117">Child Elements</span></span>  
 <span data-ttu-id="7eeeb-118">無。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7eeeb-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7eeeb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7eeeb-120">項目</span><span class="sxs-lookup"><span data-stu-id="7eeeb-120">Element</span></span>|<span data-ttu-id="7eeeb-121">說明</span><span class="sxs-lookup"><span data-stu-id="7eeeb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7eeeb-122">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="7eeeb-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7eeeb-123">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eeeb-124">備註</span><span class="sxs-lookup"><span data-stu-id="7eeeb-124">Remarks</span></span>  
 <span data-ttu-id="7eeeb-125">使用這個身分識別連接至端點的安全 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 用戶端會在對端點進行 SSPI 驗證時使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="7eeeb-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eeeb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7eeeb-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="7eeeb-127">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7eeeb-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7eeeb-128">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="7eeeb-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
