---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188242"
---
# <a name="userprincipalname"></a><span data-ttu-id="02e4c-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="02e4c-101">\<userPrincipalName></span></span>
<span data-ttu-id="02e4c-102">指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="02e4c-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="02e4c-103">如需有關設定 UPN 的詳細資訊，請參閱 <<c0> [ 服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="02e4c-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="02e4c-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="02e4c-104">\<identity></span></span>  
<span data-ttu-id="02e4c-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="02e4c-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e4c-106">語法</span><span class="sxs-lookup"><span data-stu-id="02e4c-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02e4c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02e4c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="02e4c-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="02e4c-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02e4c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="02e4c-109">Attributes</span></span>  
  
|<span data-ttu-id="02e4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="02e4c-110">Attribute</span></span>|<span data-ttu-id="02e4c-111">描述</span><span class="sxs-lookup"><span data-stu-id="02e4c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02e4c-112">value</span><span class="sxs-lookup"><span data-stu-id="02e4c-112">value</span></span>|<span data-ttu-id="02e4c-113">使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="02e4c-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="02e4c-114">這是登入 Windows 網域時的標準用法。</span><span class="sxs-lookup"><span data-stu-id="02e4c-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="02e4c-115">格式為： someone@example.com （如同電子郵件地址）。</span><span class="sxs-lookup"><span data-stu-id="02e4c-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02e4c-116">子元素</span><span class="sxs-lookup"><span data-stu-id="02e4c-116">Child Elements</span></span>  
 <span data-ttu-id="02e4c-117">無。</span><span class="sxs-lookup"><span data-stu-id="02e4c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02e4c-118">父項目</span><span class="sxs-lookup"><span data-stu-id="02e4c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="02e4c-119">項目</span><span class="sxs-lookup"><span data-stu-id="02e4c-119">Element</span></span>|<span data-ttu-id="02e4c-120">描述</span><span class="sxs-lookup"><span data-stu-id="02e4c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02e4c-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="02e4c-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="02e4c-122">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="02e4c-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02e4c-123">備註</span><span class="sxs-lookup"><span data-stu-id="02e4c-123">Remarks</span></span>  
 <span data-ttu-id="02e4c-124">安全的 Windows Communication Foundation (WCF) 用戶端連接至使用這個身分識別端點對端點進行 SSPI 驗證時，會使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="02e4c-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02e4c-125">範例</span><span class="sxs-lookup"><span data-stu-id="02e4c-125">Example</span></span>  
 <span data-ttu-id="02e4c-126">下列組態程式碼會指定要由用戶端驗證之服務的 UPN。</span><span class="sxs-lookup"><span data-stu-id="02e4c-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="02e4c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02e4c-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="02e4c-128">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="02e4c-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="02e4c-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="02e4c-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
