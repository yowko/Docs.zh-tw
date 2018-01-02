---
title: "&lt;identity&gt; 的 &lt;certificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c1fb253ed166b4e8106f68bf2782cf215541294
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="de9d4-102">&lt;identity&gt; 的 &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="de9d4-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="de9d4-103">指定向用戶端驗證伺服器時使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="de9d4-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="de9d4-104">如需有關設定項目值的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="de9d4-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="de9d4-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="de9d4-105">\<identity></span></span>  
<span data-ttu-id="de9d4-106">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="de9d4-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9d4-107">語法</span><span class="sxs-lookup"><span data-stu-id="de9d4-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de9d4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="de9d4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de9d4-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="de9d4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de9d4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="de9d4-110">Attributes</span></span>  
  
|<span data-ttu-id="de9d4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="de9d4-111">Attribute</span></span>|<span data-ttu-id="de9d4-112">描述</span><span class="sxs-lookup"><span data-stu-id="de9d4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de9d4-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="de9d4-113">encodedValue</span></span>|<span data-ttu-id="de9d4-114">憑證的 Base64 編碼。</span><span class="sxs-lookup"><span data-stu-id="de9d4-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de9d4-115">子元素</span><span class="sxs-lookup"><span data-stu-id="de9d4-115">Child Elements</span></span>  
 <span data-ttu-id="de9d4-116">無。</span><span class="sxs-lookup"><span data-stu-id="de9d4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de9d4-117">父項目</span><span class="sxs-lookup"><span data-stu-id="de9d4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="de9d4-118">項目</span><span class="sxs-lookup"><span data-stu-id="de9d4-118">Element</span></span>|<span data-ttu-id="de9d4-119">描述</span><span class="sxs-lookup"><span data-stu-id="de9d4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de9d4-120">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="de9d4-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="de9d4-121">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="de9d4-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de9d4-122">範例</span><span class="sxs-lookup"><span data-stu-id="de9d4-122">Example</span></span>  
 <span data-ttu-id="de9d4-123">下列程式碼會指定用來向用戶端驗證伺服器之憑證的編碼表示方式。</span><span class="sxs-lookup"><span data-stu-id="de9d4-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de9d4-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="de9d4-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="de9d4-125">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="de9d4-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="de9d4-126">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="de9d4-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
