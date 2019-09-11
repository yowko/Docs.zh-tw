---
title: <certificate> 的 <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850010"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="7631d-102">\<身分識別 > \<的憑證 ></span><span class="sxs-lookup"><span data-stu-id="7631d-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="7631d-103">指定向用戶端驗證伺服器時使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="7631d-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="7631d-104">如需設定元素值的詳細資訊，請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="7631d-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="7631d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7631d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7631d-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7631d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7631d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="7631d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="7631d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<端點 >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="7631d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="7631d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<身分識別 >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="7631d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="7631d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<憑證 >**</span><span class="sxs-lookup"><span data-stu-id="7631d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7631d-111">語法</span><span class="sxs-lookup"><span data-stu-id="7631d-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7631d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7631d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7631d-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7631d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7631d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7631d-114">Attributes</span></span>  
  
|<span data-ttu-id="7631d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7631d-115">Attribute</span></span>|<span data-ttu-id="7631d-116">描述</span><span class="sxs-lookup"><span data-stu-id="7631d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7631d-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="7631d-117">encodedValue</span></span>|<span data-ttu-id="7631d-118">憑證的 Base64 編碼。</span><span class="sxs-lookup"><span data-stu-id="7631d-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7631d-119">子元素</span><span class="sxs-lookup"><span data-stu-id="7631d-119">Child Elements</span></span>  
 <span data-ttu-id="7631d-120">無。</span><span class="sxs-lookup"><span data-stu-id="7631d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7631d-121">父項目</span><span class="sxs-lookup"><span data-stu-id="7631d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7631d-122">項目</span><span class="sxs-lookup"><span data-stu-id="7631d-122">Element</span></span>|<span data-ttu-id="7631d-123">描述</span><span class="sxs-lookup"><span data-stu-id="7631d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7631d-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="7631d-124">\<identity></span></span>](identity.md)|<span data-ttu-id="7631d-125">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="7631d-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7631d-126">範例</span><span class="sxs-lookup"><span data-stu-id="7631d-126">Example</span></span>  
 <span data-ttu-id="7631d-127">下列程式碼會指定用來向用戶端驗證伺服器之憑證的編碼表示方式。</span><span class="sxs-lookup"><span data-stu-id="7631d-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="7631d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7631d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="7631d-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7631d-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7631d-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="7631d-130">\<identity></span></span>](identity.md)
