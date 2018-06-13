---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 1bb0c8ac4cbe11cdfa31beb16b00b3863acabf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358673"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="45a76-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="45a76-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="45a76-103">指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="45a76-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="45a76-104">如需設定 UPN 的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="45a76-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="45a76-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="45a76-105">\<identity></span></span>  
<span data-ttu-id="45a76-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="45a76-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a76-107">語法</span><span class="sxs-lookup"><span data-stu-id="45a76-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45a76-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="45a76-108">Attributes and Elements</span></span>  
 <span data-ttu-id="45a76-109">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="45a76-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45a76-110">屬性</span><span class="sxs-lookup"><span data-stu-id="45a76-110">Attributes</span></span>  
  
|<span data-ttu-id="45a76-111">屬性</span><span class="sxs-lookup"><span data-stu-id="45a76-111">Attribute</span></span>|<span data-ttu-id="45a76-112">描述</span><span class="sxs-lookup"><span data-stu-id="45a76-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45a76-113">value</span><span class="sxs-lookup"><span data-stu-id="45a76-113">value</span></span>|<span data-ttu-id="45a76-114">使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="45a76-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="45a76-115">這是登入 Windows 網域時的標準用法。</span><span class="sxs-lookup"><span data-stu-id="45a76-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="45a76-116">格式為： someone@example.com （如同電子郵件地址）。</span><span class="sxs-lookup"><span data-stu-id="45a76-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45a76-117">子項目</span><span class="sxs-lookup"><span data-stu-id="45a76-117">Child Elements</span></span>  
 <span data-ttu-id="45a76-118">無。</span><span class="sxs-lookup"><span data-stu-id="45a76-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45a76-119">父項目</span><span class="sxs-lookup"><span data-stu-id="45a76-119">Parent Elements</span></span>  
  
|<span data-ttu-id="45a76-120">項目</span><span class="sxs-lookup"><span data-stu-id="45a76-120">Element</span></span>|<span data-ttu-id="45a76-121">描述</span><span class="sxs-lookup"><span data-stu-id="45a76-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45a76-122">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="45a76-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="45a76-123">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="45a76-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45a76-124">備註</span><span class="sxs-lookup"><span data-stu-id="45a76-124">Remarks</span></span>  
 <span data-ttu-id="45a76-125">安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點進行 SSPI 驗證與端點時，會使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="45a76-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45a76-126">範例</span><span class="sxs-lookup"><span data-stu-id="45a76-126">Example</span></span>  
 <span data-ttu-id="45a76-127">下列組態程式碼會指定要由用戶端驗證之服務的 UPN。</span><span class="sxs-lookup"><span data-stu-id="45a76-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45a76-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a76-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="45a76-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="45a76-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="45a76-130">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="45a76-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
