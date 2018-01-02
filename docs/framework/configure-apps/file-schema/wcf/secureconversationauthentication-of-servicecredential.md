---
title: "&lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f80b0570055edbe15fa467ea83e11aba2b62a8fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="1a186-102">&lt;serviceCredential&gt; 的 &lt;secureConversationAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="1a186-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="1a186-103">指定安全對話服務的設定。</span><span class="sxs-lookup"><span data-stu-id="1a186-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="1a186-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a186-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a186-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1a186-105">\<behaviors></span></span>  
<span data-ttu-id="1a186-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1a186-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1a186-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1a186-107">\<behavior></span></span>  
<span data-ttu-id="1a186-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a186-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1a186-109">\<s ></span><span class="sxs-lookup"><span data-stu-id="1a186-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a186-110">語法</span><span class="sxs-lookup"><span data-stu-id="1a186-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a186-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1a186-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1a186-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1a186-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a186-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1a186-113">Attributes</span></span>  
  
|<span data-ttu-id="1a186-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1a186-114">Attribute</span></span>|<span data-ttu-id="1a186-115">描述</span><span class="sxs-lookup"><span data-stu-id="1a186-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="1a186-116">字串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 型別。</span><span class="sxs-lookup"><span data-stu-id="1a186-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a186-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1a186-117">Child Elements</span></span>  
 <span data-ttu-id="1a186-118">無。</span><span class="sxs-lookup"><span data-stu-id="1a186-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a186-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1a186-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a186-120">項目</span><span class="sxs-lookup"><span data-stu-id="1a186-120">Element</span></span>|<span data-ttu-id="1a186-121">描述</span><span class="sxs-lookup"><span data-stu-id="1a186-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a186-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1a186-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1a186-123">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="1a186-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a186-124">備註</span><span class="sxs-lookup"><span data-stu-id="1a186-124">Remarks</span></span>  
 <span data-ttu-id="1a186-125">使用此組態項目指定安全性內容權杖 (SCT) Cookie 序列化的已知宣告型別清單，以及指定可編碼與確保 Cookie 資訊安全的編碼器。</span><span class="sxs-lookup"><span data-stu-id="1a186-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="1a186-126">如需 SCT 的詳細資訊，請參閱<xref:System.ServiceModel.Security.SecureConversationServiceCredential>。</span><span class="sxs-lookup"><span data-stu-id="1a186-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a186-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a186-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
