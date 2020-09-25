---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 353d3e2d88e3515e54deadab85c37ce3be26ef29
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203861"
---
# \<userPrincipalName>

<span data-ttu-id="1eaba-101">指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="1eaba-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="1eaba-102">如需設定 UPN 的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="1eaba-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="1eaba-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="1eaba-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1eaba-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1eaba-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1eaba-105">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1eaba-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eaba-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1eaba-106">Attributes</span></span>  
  
|<span data-ttu-id="1eaba-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1eaba-107">Attribute</span></span>|<span data-ttu-id="1eaba-108">描述</span><span class="sxs-lookup"><span data-stu-id="1eaba-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1eaba-109">value</span><span class="sxs-lookup"><span data-stu-id="1eaba-109">value</span></span>|<span data-ttu-id="1eaba-110">使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="1eaba-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="1eaba-111">這是登入 Windows 網域時的標準用法。</span><span class="sxs-lookup"><span data-stu-id="1eaba-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="1eaba-112">格式為： someone@example.com () 的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="1eaba-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1eaba-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1eaba-113">Child Elements</span></span>  

 <span data-ttu-id="1eaba-114">無。</span><span class="sxs-lookup"><span data-stu-id="1eaba-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1eaba-115">父項目</span><span class="sxs-lookup"><span data-stu-id="1eaba-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1eaba-116">項目</span><span class="sxs-lookup"><span data-stu-id="1eaba-116">Element</span></span>|<span data-ttu-id="1eaba-117">描述</span><span class="sxs-lookup"><span data-stu-id="1eaba-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="1eaba-118">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="1eaba-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eaba-119">備註</span><span class="sxs-lookup"><span data-stu-id="1eaba-119">Remarks</span></span>  

 <span data-ttu-id="1eaba-120">使用這個身分識別連接到端點的安全 Windows Communication Foundation (WCF) 用戶端，會在對端點執行 SSPI 驗證時使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="1eaba-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eaba-121">範例</span><span class="sxs-lookup"><span data-stu-id="1eaba-121">Example</span></span>  

 <span data-ttu-id="1eaba-122">下列組態程式碼會指定要由用戶端驗證之服務的 UPN。</span><span class="sxs-lookup"><span data-stu-id="1eaba-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="1eaba-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1eaba-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="1eaba-124">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="1eaba-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
