---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 0d03844a58de5b4af93f276de75c88af6efed3f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153790"
---
# \<servicePrincipalName>

<span data-ttu-id="7090f-101">由其服務原則名稱 (SPN) 指定的服務身分識別。</span><span class="sxs-lookup"><span data-stu-id="7090f-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="7090f-102">如需設定 SPN 的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="7090f-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="7090f-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="7090f-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7090f-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7090f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7090f-105">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="7090f-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7090f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="7090f-106">Attributes</span></span>  
  
|<span data-ttu-id="7090f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7090f-107">Attribute</span></span>|<span data-ttu-id="7090f-108">描述</span><span class="sxs-lookup"><span data-stu-id="7090f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7090f-109">value</span><span class="sxs-lookup"><span data-stu-id="7090f-109">value</span></span>|<span data-ttu-id="7090f-110">用戶端用於唯一識別服務執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="7090f-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="7090f-111">若您透過樹系在電腦上安裝多個服務執行個體，則每個執行個體都須有自己的 SPN。</span><span class="sxs-lookup"><span data-stu-id="7090f-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="7090f-112">若用戶端需使用多個名稱進行驗證，則指定的服務執行個體可擁有多個 SPN。</span><span class="sxs-lookup"><span data-stu-id="7090f-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7090f-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7090f-113">Child Elements</span></span>  

 <span data-ttu-id="7090f-114">無。</span><span class="sxs-lookup"><span data-stu-id="7090f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7090f-115">父項目</span><span class="sxs-lookup"><span data-stu-id="7090f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7090f-116">項目</span><span class="sxs-lookup"><span data-stu-id="7090f-116">Element</span></span>|<span data-ttu-id="7090f-117">描述</span><span class="sxs-lookup"><span data-stu-id="7090f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="7090f-118">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="7090f-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7090f-119">備註</span><span class="sxs-lookup"><span data-stu-id="7090f-119">Remarks</span></span>  

 <span data-ttu-id="7090f-120">使用這個身分識別連接到端點的安全 Windows Communication Foundation (WCF) 用戶端，會在對端點執行 SSPI 驗證時使用 SPN。</span><span class="sxs-lookup"><span data-stu-id="7090f-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7090f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7090f-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="7090f-122">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7090f-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
