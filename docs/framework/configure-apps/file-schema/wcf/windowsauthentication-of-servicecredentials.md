---
title: <windowsAuthentication> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: bda375959b535ce5f2996d594f719893164b0bd4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194995"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="3a34b-102">\<windowsAuthentication> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3a34b-102">\<windowsAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="3a34b-103">指定 Windows 服務認證的設定。</span><span class="sxs-lookup"><span data-stu-id="3a34b-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="3a34b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a34b-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a34b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a34b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3a34b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3a34b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a34b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3a34b-107">Attributes</span></span>  
  
|<span data-ttu-id="3a34b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3a34b-108">Attribute</span></span>|<span data-ttu-id="3a34b-109">描述</span><span class="sxs-lookup"><span data-stu-id="3a34b-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="3a34b-110">選擇性的布林值屬性，指定系統是否在安全性內容中包含 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="3a34b-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="3a34b-111">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="3a34b-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="3a34b-112">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="3a34b-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="3a34b-113">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a34b-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="3a34b-114">選擇性的布林值屬性，指定是否允許匿名、未經驗證的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3a34b-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="3a34b-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a34b-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3a34b-116">當繫結的 `clientCredentialType` 屬性設定為 `Windows` 時，系統不允許匿名呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3a34b-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="3a34b-117">這表示只有經過網域或工作群組驗證的呼叫端才可以存取系統。</span><span class="sxs-lookup"><span data-stu-id="3a34b-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="3a34b-118">您可以使用這個屬性覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="3a34b-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="3a34b-119">使用這個設定時需具備高度警覺。</span><span class="sxs-lookup"><span data-stu-id="3a34b-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a34b-120">子元素</span><span class="sxs-lookup"><span data-stu-id="3a34b-120">Child Elements</span></span>  

 <span data-ttu-id="3a34b-121">無。</span><span class="sxs-lookup"><span data-stu-id="3a34b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a34b-122">父項目</span><span class="sxs-lookup"><span data-stu-id="3a34b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3a34b-123">項目</span><span class="sxs-lookup"><span data-stu-id="3a34b-123">Element</span></span>|<span data-ttu-id="3a34b-124">描述</span><span class="sxs-lookup"><span data-stu-id="3a34b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="3a34b-125">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="3a34b-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a34b-126">備註</span><span class="sxs-lookup"><span data-stu-id="3a34b-126">Remarks</span></span>  

 <span data-ttu-id="3a34b-127">使用此項目並藉由設定 `allowAnonymousLogons` 屬性，指定是否允許匿名 Windows 使用者存取。</span><span class="sxs-lookup"><span data-stu-id="3a34b-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="3a34b-128">您也可以藉由設定 `includeWindowsGroups` 屬性，指定是否要在 AuthorizationContext 中包含使用者所屬群組的資訊。</span><span class="sxs-lookup"><span data-stu-id="3a34b-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="3a34b-129">如果該屬性設為 `true` (預設值)，服務就可以判斷用戶端屬於哪個 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="3a34b-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a34b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a34b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
