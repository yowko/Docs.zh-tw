---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 1698ce421b4dcefc6ab94206443d2d7bca47aca8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162279"
---
# \<rsa>

<span data-ttu-id="228de-101">使用這個身分識別連接至端點的安全 WCF 用戶端，將確認伺服器提供的宣告是否包含用來建構這個身分識別之 RSA 公開金鑰的宣告。</span><span class="sxs-lookup"><span data-stu-id="228de-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="228de-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="228de-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="228de-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="228de-103">Attributes and Elements</span></span>  

 <span data-ttu-id="228de-104">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="228de-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="228de-105">屬性</span><span class="sxs-lookup"><span data-stu-id="228de-105">Attributes</span></span>  
  
|<span data-ttu-id="228de-106">屬性</span><span class="sxs-lookup"><span data-stu-id="228de-106">Attribute</span></span>|<span data-ttu-id="228de-107">描述</span><span class="sxs-lookup"><span data-stu-id="228de-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="228de-108">value</span><span class="sxs-lookup"><span data-stu-id="228de-108">value</span></span>|<span data-ttu-id="228de-109">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="228de-109">Optional String.</span></span> <span data-ttu-id="228de-110">在用戶端上要比對的 RSA 公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="228de-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="228de-111">子元素</span><span class="sxs-lookup"><span data-stu-id="228de-111">Child Elements</span></span>  

 <span data-ttu-id="228de-112">無</span><span class="sxs-lookup"><span data-stu-id="228de-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="228de-113">父項目</span><span class="sxs-lookup"><span data-stu-id="228de-113">Parent Elements</span></span>  
  
|<span data-ttu-id="228de-114">項目</span><span class="sxs-lookup"><span data-stu-id="228de-114">Element</span></span>|<span data-ttu-id="228de-115">描述</span><span class="sxs-lookup"><span data-stu-id="228de-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="228de-116">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="228de-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228de-117">備註</span><span class="sxs-lookup"><span data-stu-id="228de-117">Remarks</span></span>  

 <span data-ttu-id="228de-118">RSA 檢查可讓您根據其 RSA 金鑰或所產生之您自己的 RSA 金鑰值，特別將驗證限制為單一憑證。</span><span class="sxs-lookup"><span data-stu-id="228de-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="228de-119">如此，若 RSA 金鑰值變更了，特定 RSA 金鑰隨即達成更嚴格的驗證，但該服務便無法和現有用戶端運作。</span><span class="sxs-lookup"><span data-stu-id="228de-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="228de-120">如需使用身分識別來向用戶端驗證服務的詳細資訊，請參閱 [服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="228de-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="228de-121">範例</span><span class="sxs-lookup"><span data-stu-id="228de-121">Example</span></span>  

 <span data-ttu-id="228de-122">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="228de-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="228de-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="228de-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="228de-124">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="228de-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
