---
title: <certificate> 為 <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 24c39b5efaee7f8db12088d272efeb3783efab04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198856"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="1dfa9-102">\<certificate> 為 \<identity></span><span class="sxs-lookup"><span data-stu-id="1dfa9-102">\<certificate> for \<identity></span></span>

<span data-ttu-id="1dfa9-103">指定向用戶端驗證伺服器時使用的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="1dfa9-104">如需設定元素值的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="1dfa9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dfa9-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dfa9-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dfa9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="1dfa9-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dfa9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1dfa9-108">Attributes</span></span>  
  
|<span data-ttu-id="1dfa9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="1dfa9-109">Attribute</span></span>|<span data-ttu-id="1dfa9-110">描述</span><span class="sxs-lookup"><span data-stu-id="1dfa9-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1dfa9-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="1dfa9-111">encodedValue</span></span>|<span data-ttu-id="1dfa9-112">憑證的 Base64 編碼。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1dfa9-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1dfa9-113">Child Elements</span></span>  

 <span data-ttu-id="1dfa9-114">無。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1dfa9-115">父項目</span><span class="sxs-lookup"><span data-stu-id="1dfa9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1dfa9-116">項目</span><span class="sxs-lookup"><span data-stu-id="1dfa9-116">Element</span></span>|<span data-ttu-id="1dfa9-117">描述</span><span class="sxs-lookup"><span data-stu-id="1dfa9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="1dfa9-118">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1dfa9-119">範例</span><span class="sxs-lookup"><span data-stu-id="1dfa9-119">Example</span></span>  

 <span data-ttu-id="1dfa9-120">下列程式碼會指定用來向用戶端驗證伺服器之憑證的編碼表示方式。</span><span class="sxs-lookup"><span data-stu-id="1dfa9-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="1dfa9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dfa9-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="1dfa9-122">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="1dfa9-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
