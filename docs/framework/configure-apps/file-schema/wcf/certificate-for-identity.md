---
title: <certificate> 的 <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 52d1fa31cebd949c91809464976739ef1334af29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919608"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="33e8a-102">\<身分識別 > \<的憑證 ></span><span class="sxs-lookup"><span data-stu-id="33e8a-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="33e8a-103">指定向用戶端驗證伺服器時使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="33e8a-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="33e8a-104">如需設定元素值的詳細資訊, 請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="33e8a-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="33e8a-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="33e8a-105">\<identity></span></span>  
<span data-ttu-id="33e8a-106">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="33e8a-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e8a-107">語法</span><span class="sxs-lookup"><span data-stu-id="33e8a-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33e8a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="33e8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="33e8a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="33e8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33e8a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="33e8a-110">Attributes</span></span>  
  
|<span data-ttu-id="33e8a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="33e8a-111">Attribute</span></span>|<span data-ttu-id="33e8a-112">描述</span><span class="sxs-lookup"><span data-stu-id="33e8a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33e8a-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="33e8a-113">encodedValue</span></span>|<span data-ttu-id="33e8a-114">憑證的 Base64 編碼。</span><span class="sxs-lookup"><span data-stu-id="33e8a-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33e8a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="33e8a-115">Child Elements</span></span>  
 <span data-ttu-id="33e8a-116">無。</span><span class="sxs-lookup"><span data-stu-id="33e8a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33e8a-117">父項目</span><span class="sxs-lookup"><span data-stu-id="33e8a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="33e8a-118">項目</span><span class="sxs-lookup"><span data-stu-id="33e8a-118">Element</span></span>|<span data-ttu-id="33e8a-119">描述</span><span class="sxs-lookup"><span data-stu-id="33e8a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33e8a-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="33e8a-120">\<identity></span></span>](identity.md)|<span data-ttu-id="33e8a-121">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="33e8a-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="33e8a-122">範例</span><span class="sxs-lookup"><span data-stu-id="33e8a-122">Example</span></span>  
 <span data-ttu-id="33e8a-123">下列程式碼會指定用來向用戶端驗證伺服器之憑證的編碼表示方式。</span><span class="sxs-lookup"><span data-stu-id="33e8a-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="33e8a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e8a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="33e8a-125">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="33e8a-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="33e8a-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="33e8a-126">\<identity></span></span>](identity.md)
