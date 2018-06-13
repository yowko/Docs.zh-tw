---
title: '&lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7b56d12793ad35e6f951638465e77b92a66a6fd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749328"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="7535a-102">&lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="7535a-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="7535a-103">指定安全對話服務的設定。</span><span class="sxs-lookup"><span data-stu-id="7535a-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="7535a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7535a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7535a-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7535a-105">\<behaviors></span></span>  
<span data-ttu-id="7535a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7535a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7535a-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7535a-107">\<behavior></span></span>  
<span data-ttu-id="7535a-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7535a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7535a-109">\<s ></span><span class="sxs-lookup"><span data-stu-id="7535a-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7535a-110">語法</span><span class="sxs-lookup"><span data-stu-id="7535a-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7535a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7535a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7535a-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7535a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7535a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7535a-113">Attributes</span></span>  
  
|<span data-ttu-id="7535a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7535a-114">Attribute</span></span>|<span data-ttu-id="7535a-115">描述</span><span class="sxs-lookup"><span data-stu-id="7535a-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="7535a-116">字串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 型別。</span><span class="sxs-lookup"><span data-stu-id="7535a-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7535a-117">子項目</span><span class="sxs-lookup"><span data-stu-id="7535a-117">Child Elements</span></span>  
 <span data-ttu-id="7535a-118">無。</span><span class="sxs-lookup"><span data-stu-id="7535a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7535a-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7535a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7535a-120">項目</span><span class="sxs-lookup"><span data-stu-id="7535a-120">Element</span></span>|<span data-ttu-id="7535a-121">描述</span><span class="sxs-lookup"><span data-stu-id="7535a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7535a-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7535a-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="7535a-123">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="7535a-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7535a-124">備註</span><span class="sxs-lookup"><span data-stu-id="7535a-124">Remarks</span></span>  
 <span data-ttu-id="7535a-125">使用此組態項目指定安全性內容權杖 (SCT) Cookie 序列化的已知宣告型別清單，以及指定可編碼與確保 Cookie 資訊安全的編碼器。</span><span class="sxs-lookup"><span data-stu-id="7535a-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="7535a-126">如需 SCT 的詳細資訊，請參閱<xref:System.ServiceModel.Security.SecureConversationServiceCredential>。</span><span class="sxs-lookup"><span data-stu-id="7535a-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7535a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7535a-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
