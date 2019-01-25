---
title: '&lt;rsa&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 74da1e2ae02f151f928afec24d6af3adf703bdcd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612783"
---
# <a name="ltrsagt"></a><span data-ttu-id="f6779-102">&lt;rsa&gt;</span><span class="sxs-lookup"><span data-stu-id="f6779-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="f6779-103">使用這個身分識別連接至端點的安全 WCF 用戶端，將確認伺服器提供的宣告是否包含用來建構這個身分識別之 RSA 公開金鑰的宣告。</span><span class="sxs-lookup"><span data-stu-id="f6779-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="f6779-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="f6779-104">\<identity></span></span>  
<span data-ttu-id="f6779-105">\<rsa></span><span class="sxs-lookup"><span data-stu-id="f6779-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6779-106">語法</span><span class="sxs-lookup"><span data-stu-id="f6779-106">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6779-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6779-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f6779-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f6779-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6779-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f6779-109">Attributes</span></span>  
  
|<span data-ttu-id="f6779-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f6779-110">Attribute</span></span>|<span data-ttu-id="f6779-111">描述</span><span class="sxs-lookup"><span data-stu-id="f6779-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6779-112">value</span><span class="sxs-lookup"><span data-stu-id="f6779-112">value</span></span>|<span data-ttu-id="f6779-113">選擇性字串。</span><span class="sxs-lookup"><span data-stu-id="f6779-113">Optional String.</span></span> <span data-ttu-id="f6779-114">在用戶端上要比對的 RSA 公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="f6779-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6779-115">子元素</span><span class="sxs-lookup"><span data-stu-id="f6779-115">Child Elements</span></span>  
 <span data-ttu-id="f6779-116">無</span><span class="sxs-lookup"><span data-stu-id="f6779-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6779-117">父項目</span><span class="sxs-lookup"><span data-stu-id="f6779-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f6779-118">項目</span><span class="sxs-lookup"><span data-stu-id="f6779-118">Element</span></span>|<span data-ttu-id="f6779-119">描述</span><span class="sxs-lookup"><span data-stu-id="f6779-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6779-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="f6779-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="f6779-121">指定要由用戶端驗證之服務的身分識別。</span><span class="sxs-lookup"><span data-stu-id="f6779-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6779-122">備註</span><span class="sxs-lookup"><span data-stu-id="f6779-122">Remarks</span></span>  
 <span data-ttu-id="f6779-123">RSA 檢查可讓您根據其 RSA 金鑰或所產生之您自己的 RSA 金鑰值，特別將驗證限制為單一憑證。</span><span class="sxs-lookup"><span data-stu-id="f6779-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="f6779-124">如此，若 RSA 金鑰值變更了，特定 RSA 金鑰隨即達成更嚴格的驗證，但該服務便無法和現有用戶端運作。</span><span class="sxs-lookup"><span data-stu-id="f6779-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="f6779-125">如需使用身分識別來驗證用戶端服務的詳細資訊，請參閱[服務身分識別和驗證](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="f6779-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6779-126">範例</span><span class="sxs-lookup"><span data-stu-id="f6779-126">Example</span></span>  
 <span data-ttu-id="f6779-127">下列組態程式碼會指定用來驗證伺服器之 X.509 憑證的公開金鑰值。</span><span class="sxs-lookup"><span data-stu-id="f6779-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="f6779-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6779-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="f6779-129">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="f6779-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f6779-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="f6779-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
