---
title: <windowsAuthentication> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399104"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="9c68c-102">\<serviceCredentials > 的\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="9c68c-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="9c68c-103">指定 Windows 服務認證的設定。</span><span class="sxs-lookup"><span data-stu-id="9c68c-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="9c68c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9c68c-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9c68c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9c68c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9c68c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9c68c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9c68c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="9c68c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="9c68c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c68c-111">語法</span><span class="sxs-lookup"><span data-stu-id="9c68c-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c68c-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9c68c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9c68c-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9c68c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c68c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9c68c-114">Attributes</span></span>  
  
|<span data-ttu-id="9c68c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="9c68c-115">Attribute</span></span>|<span data-ttu-id="9c68c-116">描述</span><span class="sxs-lookup"><span data-stu-id="9c68c-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="9c68c-117">選擇性的布林值屬性，指定系統是否在安全性內容中包含 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="9c68c-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="9c68c-118">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="9c68c-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="9c68c-119">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="9c68c-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="9c68c-120">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9c68c-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="9c68c-121">選擇性的布林值屬性，指定是否允許匿名、未經驗證的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="9c68c-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="9c68c-122">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9c68c-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9c68c-123">當繫結的 `clientCredentialType` 屬性設定為 `Windows` 時，系統不允許匿名呼叫端。</span><span class="sxs-lookup"><span data-stu-id="9c68c-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="9c68c-124">這表示只有經過網域或工作群組驗證的呼叫端才可以存取系統。</span><span class="sxs-lookup"><span data-stu-id="9c68c-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="9c68c-125">您可以使用這個屬性覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="9c68c-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="9c68c-126">使用這個設定時需具備高度警覺。</span><span class="sxs-lookup"><span data-stu-id="9c68c-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c68c-127">子元素</span><span class="sxs-lookup"><span data-stu-id="9c68c-127">Child Elements</span></span>  
 <span data-ttu-id="9c68c-128">無。</span><span class="sxs-lookup"><span data-stu-id="9c68c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c68c-129">父項目</span><span class="sxs-lookup"><span data-stu-id="9c68c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9c68c-130">項目</span><span class="sxs-lookup"><span data-stu-id="9c68c-130">Element</span></span>|<span data-ttu-id="9c68c-131">描述</span><span class="sxs-lookup"><span data-stu-id="9c68c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c68c-132">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9c68c-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="9c68c-133">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="9c68c-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c68c-134">備註</span><span class="sxs-lookup"><span data-stu-id="9c68c-134">Remarks</span></span>  
 <span data-ttu-id="9c68c-135">使用此項目並藉由設定 `allowAnonymousLogons` 屬性，指定是否允許匿名 Windows 使用者存取。</span><span class="sxs-lookup"><span data-stu-id="9c68c-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="9c68c-136">您也可以藉由設定 `includeWindowsGroups` 屬性，指定是否要在 AuthorizationContext 中包含使用者所屬群組的資訊。</span><span class="sxs-lookup"><span data-stu-id="9c68c-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="9c68c-137">如果該屬性設為 `true` (預設值)，服務就可以判斷用戶端屬於哪個 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="9c68c-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c68c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c68c-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
