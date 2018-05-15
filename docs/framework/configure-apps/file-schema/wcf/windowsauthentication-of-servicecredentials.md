---
title: '&lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt; '
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 9872b1f2520661ff3f31cef94b6822bb345ebfdf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="7df3f-102">&lt;serviceCredentials&gt; 的 &lt;windowsAuthentication&gt; </span><span class="sxs-lookup"><span data-stu-id="7df3f-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="7df3f-103">指定 Windows 服務認證的設定。</span><span class="sxs-lookup"><span data-stu-id="7df3f-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="7df3f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7df3f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7df3f-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7df3f-105">\<behaviors></span></span>  
<span data-ttu-id="7df3f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7df3f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7df3f-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7df3f-107">\<behavior></span></span>  
<span data-ttu-id="7df3f-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7df3f-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7df3f-109">\<windows 驗證 ></span><span class="sxs-lookup"><span data-stu-id="7df3f-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df3f-110">語法</span><span class="sxs-lookup"><span data-stu-id="7df3f-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7df3f-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7df3f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7df3f-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7df3f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7df3f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7df3f-113">Attributes</span></span>  
  
|<span data-ttu-id="7df3f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7df3f-114">Attribute</span></span>|<span data-ttu-id="7df3f-115">描述</span><span class="sxs-lookup"><span data-stu-id="7df3f-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="7df3f-116">選擇性的布林值屬性，指定系統是否在安全性內容中包含 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="7df3f-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="7df3f-117">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7df3f-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="7df3f-118">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="7df3f-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="7df3f-119">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7df3f-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="7df3f-120">選擇性的布林值屬性，指定是否允許匿名、未經驗證的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7df3f-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="7df3f-121">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7df3f-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7df3f-122">當繫結的 `clientCredentialType` 屬性設定為 `Windows` 時，系統不允許匿名呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7df3f-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="7df3f-123">這表示只有經過網域或工作群組驗證的呼叫端才可以存取系統。</span><span class="sxs-lookup"><span data-stu-id="7df3f-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="7df3f-124">您可以使用這個屬性覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="7df3f-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="7df3f-125">使用這個設定時需具備高度警覺。</span><span class="sxs-lookup"><span data-stu-id="7df3f-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7df3f-126">子項目</span><span class="sxs-lookup"><span data-stu-id="7df3f-126">Child Elements</span></span>  
 <span data-ttu-id="7df3f-127">無。</span><span class="sxs-lookup"><span data-stu-id="7df3f-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7df3f-128">父項目</span><span class="sxs-lookup"><span data-stu-id="7df3f-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7df3f-129">項目</span><span class="sxs-lookup"><span data-stu-id="7df3f-129">Element</span></span>|<span data-ttu-id="7df3f-130">描述</span><span class="sxs-lookup"><span data-stu-id="7df3f-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7df3f-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7df3f-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="7df3f-132">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="7df3f-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7df3f-133">備註</span><span class="sxs-lookup"><span data-stu-id="7df3f-133">Remarks</span></span>  
 <span data-ttu-id="7df3f-134">使用此項目並藉由設定 `allowAnonymousLogons` 屬性，指定是否允許匿名 Windows 使用者存取。</span><span class="sxs-lookup"><span data-stu-id="7df3f-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="7df3f-135">您也可以藉由設定 `includeWindowsGroups` 屬性，指定是否要在 AuthorizationContext 中包含使用者所屬群組的資訊。</span><span class="sxs-lookup"><span data-stu-id="7df3f-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="7df3f-136">如果該屬性設為 `true` (預設值)，服務就可以判斷用戶端屬於哪個 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="7df3f-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df3f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df3f-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>
