---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934742"
---
# <a name="rsa"></a><span data-ttu-id="d1f6e-101">\<rsa ></span><span class="sxs-lookup"><span data-stu-id="d1f6e-101">\<rsa></span></span>
<span data-ttu-id="d1f6e-102">使用這個身分識別連接至端點的安全 WCF 用戶端，將確認伺服器提供的宣告是否包含用來建構這個身分識別之 RSA 公開金鑰的宣告。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="d1f6e-103">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="d1f6e-103">\<identity></span></span>  
<span data-ttu-id="d1f6e-104">\<rsa ></span><span class="sxs-lookup"><span data-stu-id="d1f6e-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f6e-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1f6e-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1f6e-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1f6e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d1f6e-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d1f6e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1f6e-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d1f6e-108">Attributes</span></span>  
  
|<span data-ttu-id="d1f6e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d1f6e-109">Attribute</span></span>|<span data-ttu-id="d1f6e-110">說明</span><span class="sxs-lookup"><span data-stu-id="d1f6e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1f6e-111">value</span><span class="sxs-lookup"><span data-stu-id="d1f6e-111">value</span></span>|<span data-ttu-id="d1f6e-112">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-112">Optional String.</span></span> <span data-ttu-id="d1f6e-113">在用戶端上要比對的 RSA 公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1f6e-114">子元素</span><span class="sxs-lookup"><span data-stu-id="d1f6e-114">Child Elements</span></span>  
 <span data-ttu-id="d1f6e-115">None</span><span class="sxs-lookup"><span data-stu-id="d1f6e-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1f6e-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d1f6e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d1f6e-117">項目</span><span class="sxs-lookup"><span data-stu-id="d1f6e-117">Element</span></span>|<span data-ttu-id="d1f6e-118">說明</span><span class="sxs-lookup"><span data-stu-id="d1f6e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1f6e-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1f6e-119">\<identity></span></span>](identity.md)|<span data-ttu-id="d1f6e-120">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f6e-121">備註</span><span class="sxs-lookup"><span data-stu-id="d1f6e-121">Remarks</span></span>  
 <span data-ttu-id="d1f6e-122">RSA 檢查可讓您根據其 RSA 金鑰或所產生之您自己的 RSA 金鑰值，特別將驗證限制為單一憑證。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="d1f6e-123">如此，若 RSA 金鑰值變更了，特定 RSA 金鑰隨即達成更嚴格的驗證，但該服務便無法和現有用戶端運作。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="d1f6e-124">如需使用身分識別向用戶端驗證服務的詳細資訊, 請參閱[服務身分識別和驗證](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1f6e-125">範例</span><span class="sxs-lookup"><span data-stu-id="d1f6e-125">Example</span></span>  
 <span data-ttu-id="d1f6e-126">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="d1f6e-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="d1f6e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1f6e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="d1f6e-128">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d1f6e-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d1f6e-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="d1f6e-129">\<identity></span></span>](identity.md)
