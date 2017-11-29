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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="56269-102">&lt;identity&gt; 的 &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="56269-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="56269-103">指定向用戶端驗證伺服器時使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="56269-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="56269-104">如需有關設定項目值的詳細資訊，請參閱[服務識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="56269-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="56269-105">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="56269-105">\<identity></span></span>  
<span data-ttu-id="56269-106">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="56269-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56269-107">語法</span><span class="sxs-lookup"><span data-stu-id="56269-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56269-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="56269-108">Attributes and Elements</span></span>  
 <span data-ttu-id="56269-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="56269-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56269-110">屬性</span><span class="sxs-lookup"><span data-stu-id="56269-110">Attributes</span></span>  
  
|<span data-ttu-id="56269-111">屬性</span><span class="sxs-lookup"><span data-stu-id="56269-111">Attribute</span></span>|<span data-ttu-id="56269-112">描述</span><span class="sxs-lookup"><span data-stu-id="56269-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56269-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="56269-113">encodedValue</span></span>|<span data-ttu-id="56269-114">憑證的 Base64 編碼。</span><span class="sxs-lookup"><span data-stu-id="56269-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56269-115">子元素</span><span class="sxs-lookup"><span data-stu-id="56269-115">Child Elements</span></span>  
 <span data-ttu-id="56269-116">無。</span><span class="sxs-lookup"><span data-stu-id="56269-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56269-117">父項目</span><span class="sxs-lookup"><span data-stu-id="56269-117">Parent Elements</span></span>  
  
|<span data-ttu-id="56269-118">項目</span><span class="sxs-lookup"><span data-stu-id="56269-118">Element</span></span>|<span data-ttu-id="56269-119">說明</span><span class="sxs-lookup"><span data-stu-id="56269-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56269-120">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="56269-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="56269-121">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="56269-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="56269-122">範例</span><span class="sxs-lookup"><span data-stu-id="56269-122">Example</span></span>  
 <span data-ttu-id="56269-123">下列程式碼會指定用來向用戶端驗證伺服器之憑證的編碼表示方式。</span><span class="sxs-lookup"><span data-stu-id="56269-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56269-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56269-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="56269-125">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="56269-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="56269-126">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="56269-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
