---
title: "&lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt; "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b6043b35ea9dbed1e1e6e170035436038334b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="0d4cf-102">&lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt; </span><span class="sxs-lookup"><span data-stu-id="0d4cf-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="0d4cf-103">指定 Windows 服務認證的設定。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="0d4cf-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d4cf-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-105">\<behaviors></span></span>  
<span data-ttu-id="0d4cf-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0d4cf-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-107">\<behavior></span></span>  
<span data-ttu-id="0d4cf-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-108">\<serviceCredentials></span></span>  
<span data-ttu-id="0d4cf-109">\<windows 驗證 ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4cf-110">語法</span><span class="sxs-lookup"><span data-stu-id="0d4cf-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d4cf-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d4cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0d4cf-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d4cf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0d4cf-113">Attributes</span></span>  
  
|<span data-ttu-id="0d4cf-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0d4cf-114">Attribute</span></span>|<span data-ttu-id="0d4cf-115">描述</span><span class="sxs-lookup"><span data-stu-id="0d4cf-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="0d4cf-116">選擇性的布林值屬性，指定系統是否在安全性內容中包含 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="0d4cf-117">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="0d4cf-118">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="0d4cf-119">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="0d4cf-120">選擇性的布林值屬性，指定是否允許匿名、未經驗證的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="0d4cf-121">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="0d4cf-122">當繫結的 `clientCredentialType` 屬性設定為 `Windows` 時，系統不允許匿名呼叫端。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="0d4cf-123">這表示只有經過網域或工作群組驗證的呼叫端才可以存取系統。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="0d4cf-124">您可以使用這個屬性覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="0d4cf-125">使用這個設定時需具備高度警覺。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d4cf-126">子元素</span><span class="sxs-lookup"><span data-stu-id="0d4cf-126">Child Elements</span></span>  
 <span data-ttu-id="0d4cf-127">無。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d4cf-128">父項目</span><span class="sxs-lookup"><span data-stu-id="0d4cf-128">Parent Elements</span></span>  
  
|<span data-ttu-id="0d4cf-129">項目</span><span class="sxs-lookup"><span data-stu-id="0d4cf-129">Element</span></span>|<span data-ttu-id="0d4cf-130">描述</span><span class="sxs-lookup"><span data-stu-id="0d4cf-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d4cf-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0d4cf-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="0d4cf-132">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d4cf-133">備註</span><span class="sxs-lookup"><span data-stu-id="0d4cf-133">Remarks</span></span>  
 <span data-ttu-id="0d4cf-134">使用此項目並藉由設定 `allowAnonymousLogons` 屬性，指定是否允許匿名 Windows 使用者存取。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="0d4cf-135">您也可以藉由設定 `includeWindowsGroups` 屬性，指定是否要在 AuthorizationContext 中包含使用者所屬群組的資訊。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="0d4cf-136">如果該屬性設為 `true` (預設值)，服務就可以判斷用戶端屬於哪個 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="0d4cf-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4cf-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d4cf-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
