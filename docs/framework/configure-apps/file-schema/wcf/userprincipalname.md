---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854831"
---
# <a name="userprincipalname"></a><span data-ttu-id="38e97-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="38e97-101">\<userPrincipalName></span></span>
<span data-ttu-id="38e97-102">指定要由用戶端驗證之服務的使用者主要名稱 (UPN)。</span><span class="sxs-lookup"><span data-stu-id="38e97-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="38e97-103">如需設定 UPN 的詳細資訊，請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="38e97-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="38e97-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38e97-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38e97-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38e97-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38e97-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="38e97-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="38e97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="38e97-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="38e97-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<身分識別 >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="38e97-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="38e97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userPrincipalName >**</span><span class="sxs-lookup"><span data-stu-id="38e97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e97-110">語法</span><span class="sxs-lookup"><span data-stu-id="38e97-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38e97-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38e97-111">Attributes and Elements</span></span>  
 <span data-ttu-id="38e97-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="38e97-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38e97-113">屬性</span><span class="sxs-lookup"><span data-stu-id="38e97-113">Attributes</span></span>  
  
|<span data-ttu-id="38e97-114">屬性</span><span class="sxs-lookup"><span data-stu-id="38e97-114">Attribute</span></span>|<span data-ttu-id="38e97-115">說明</span><span class="sxs-lookup"><span data-stu-id="38e97-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38e97-116">value</span><span class="sxs-lookup"><span data-stu-id="38e97-116">value</span></span>|<span data-ttu-id="38e97-117">使用者帳戶名稱 (有時稱為使用者登入名稱) 和識別使用者帳戶所在網域的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="38e97-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="38e97-118">這是登入 Windows 網域時的標準用法。</span><span class="sxs-lookup"><span data-stu-id="38e97-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="38e97-119">格式為： someone@example.com （如電子郵件地址）。</span><span class="sxs-lookup"><span data-stu-id="38e97-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38e97-120">子元素</span><span class="sxs-lookup"><span data-stu-id="38e97-120">Child Elements</span></span>  
 <span data-ttu-id="38e97-121">無。</span><span class="sxs-lookup"><span data-stu-id="38e97-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38e97-122">父項目</span><span class="sxs-lookup"><span data-stu-id="38e97-122">Parent Elements</span></span>  
  
|<span data-ttu-id="38e97-123">項目</span><span class="sxs-lookup"><span data-stu-id="38e97-123">Element</span></span>|<span data-ttu-id="38e97-124">說明</span><span class="sxs-lookup"><span data-stu-id="38e97-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38e97-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="38e97-125">\<identity></span></span>](identity.md)|<span data-ttu-id="38e97-126">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="38e97-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e97-127">備註</span><span class="sxs-lookup"><span data-stu-id="38e97-127">Remarks</span></span>  
 <span data-ttu-id="38e97-128">使用此身分識別連接到端點的安全 Windows Communication Foundation （WCF）用戶端會在對端點執行 SSPI 驗證時使用 UPN。</span><span class="sxs-lookup"><span data-stu-id="38e97-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38e97-129">範例</span><span class="sxs-lookup"><span data-stu-id="38e97-129">Example</span></span>  
 <span data-ttu-id="38e97-130">下列組態程式碼會指定要由用戶端驗證之服務的 UPN。</span><span class="sxs-lookup"><span data-stu-id="38e97-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="38e97-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38e97-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="38e97-132">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="38e97-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="38e97-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="38e97-133">\<identity></span></span>](identity.md)
