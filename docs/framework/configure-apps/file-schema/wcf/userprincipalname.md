---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940517"
---
# <a name="userprincipalname"></a><span data-ttu-id="f418b-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="f418b-101">\<userPrincipalName></span></span>
<span data-ttu-id="f418b-102">指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="f418b-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="f418b-103">如需設定 UPN 的詳細資訊, 請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="f418b-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="f418b-104">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="f418b-104">\<identity></span></span>  
<span data-ttu-id="f418b-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="f418b-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f418b-106">語法</span><span class="sxs-lookup"><span data-stu-id="f418b-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f418b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f418b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f418b-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f418b-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f418b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f418b-109">Attributes</span></span>  
  
|<span data-ttu-id="f418b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f418b-110">Attribute</span></span>|<span data-ttu-id="f418b-111">描述</span><span class="sxs-lookup"><span data-stu-id="f418b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f418b-112">value</span><span class="sxs-lookup"><span data-stu-id="f418b-112">value</span></span>|<span data-ttu-id="f418b-113">使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f418b-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="f418b-114">這是登入 Windows 網域時的標準用法。</span><span class="sxs-lookup"><span data-stu-id="f418b-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="f418b-115">格式為: someone@example.com (如電子郵件地址)。</span><span class="sxs-lookup"><span data-stu-id="f418b-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f418b-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f418b-116">Child Elements</span></span>  
 <span data-ttu-id="f418b-117">無。</span><span class="sxs-lookup"><span data-stu-id="f418b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f418b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f418b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f418b-119">項目</span><span class="sxs-lookup"><span data-stu-id="f418b-119">Element</span></span>|<span data-ttu-id="f418b-120">說明</span><span class="sxs-lookup"><span data-stu-id="f418b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f418b-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="f418b-121">\<identity></span></span>](identity.md)|<span data-ttu-id="f418b-122">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="f418b-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f418b-123">備註</span><span class="sxs-lookup"><span data-stu-id="f418b-123">Remarks</span></span>  
 <span data-ttu-id="f418b-124">使用此身分識別連接到端點的安全 Windows Communication Foundation (WCF) 用戶端會在對端點執行 SSPI 驗證時使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="f418b-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f418b-125">範例</span><span class="sxs-lookup"><span data-stu-id="f418b-125">Example</span></span>  
 <span data-ttu-id="f418b-126">下列組態程式碼會指定要由用戶端驗證之服務的 UPN。</span><span class="sxs-lookup"><span data-stu-id="f418b-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="f418b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f418b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="f418b-128">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="f418b-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f418b-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="f418b-129">\<identity></span></span>](identity.md)
