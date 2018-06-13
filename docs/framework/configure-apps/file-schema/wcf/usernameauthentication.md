---
title: '&lt;userNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: d81bf3441f4999683b9dc9ab956fff517c20e80e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754859"
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="ef180-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="ef180-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="ef180-103">根據使用者名稱和密碼來指定服務的認證。</span><span class="sxs-lookup"><span data-stu-id="ef180-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="ef180-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef180-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef180-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ef180-105">\<behaviors></span></span>  
<span data-ttu-id="ef180-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ef180-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ef180-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="ef180-107">\<behavior></span></span>  
<span data-ttu-id="ef180-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ef180-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ef180-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ef180-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef180-110">語法</span><span class="sxs-lookup"><span data-stu-id="ef180-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
   cacheLogonTokens="Boolean"   
   customUserNamePasswordValidatorType="String"  
   includeWindowsGroups="Boolean"   
   maxCacheLogonTokens="Integer"  
   membershipProviderName="String"  
   userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef180-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ef180-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ef180-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ef180-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef180-113">屬性</span><span class="sxs-lookup"><span data-stu-id="ef180-113">Attributes</span></span>  
  
|<span data-ttu-id="ef180-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ef180-114">Attribute</span></span>|<span data-ttu-id="ef180-115">描述</span><span class="sxs-lookup"><span data-stu-id="ef180-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="ef180-116"><xref:System.TimeSpan>，指定快取權杖的最大時間長度。</span><span class="sxs-lookup"><span data-stu-id="ef180-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="ef180-117">預設為 00:15:00。</span><span class="sxs-lookup"><span data-stu-id="ef180-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="ef180-118">布林值，指定是否要快取登入權杖。</span><span class="sxs-lookup"><span data-stu-id="ef180-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="ef180-119">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ef180-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="ef180-120">字串，指定所使用的自訂使用者名稱密碼驗證程式的型別。</span><span class="sxs-lookup"><span data-stu-id="ef180-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="ef180-121">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="ef180-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="ef180-122">布林值，指定 Windows 群組是否包含在安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="ef180-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="ef180-123">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="ef180-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="ef180-124">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="ef180-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="ef180-125">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ef180-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="ef180-126">整數，指定快取登入權杖的數目上限。</span><span class="sxs-lookup"><span data-stu-id="ef180-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="ef180-127">這個值應大於零。</span><span class="sxs-lookup"><span data-stu-id="ef180-127">This value should be larger than zero.</span></span> <span data-ttu-id="ef180-128">預設值為 128。</span><span class="sxs-lookup"><span data-stu-id="ef180-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="ef180-129">當繫結的 `clientCredentialType` 屬性設為 `username` 時，使用者名稱會對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="ef180-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="ef180-130">您可以使用這個屬性來覆寫這個行為，該屬性是一個字串，其中包含 <xref:System.Web.Security.MembershipProvider> 值的名稱，可提供相關的密碼驗證機制。</span><span class="sxs-lookup"><span data-stu-id="ef180-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="ef180-131">指定驗證使用者名稱密碼的方法。</span><span class="sxs-lookup"><span data-stu-id="ef180-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="ef180-132">有效值為：</span><span class="sxs-lookup"><span data-stu-id="ef180-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="ef180-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="ef180-133">-   Windows</span></span><br /><span data-ttu-id="ef180-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="ef180-134">-   MembershipProvider</span></span><br /><span data-ttu-id="ef180-135">自訂</span><span class="sxs-lookup"><span data-stu-id="ef180-135">-   Custom</span></span><br /><br /> <span data-ttu-id="ef180-136">預設為 Windows。</span><span class="sxs-lookup"><span data-stu-id="ef180-136">The default is Windows.</span></span> <span data-ttu-id="ef180-137">此屬性的型別為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="ef180-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef180-138">子項目</span><span class="sxs-lookup"><span data-stu-id="ef180-138">Child Elements</span></span>  
 <span data-ttu-id="ef180-139">無。</span><span class="sxs-lookup"><span data-stu-id="ef180-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef180-140">父項目</span><span class="sxs-lookup"><span data-stu-id="ef180-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ef180-141">項目</span><span class="sxs-lookup"><span data-stu-id="ef180-141">Element</span></span>|<span data-ttu-id="ef180-142">描述</span><span class="sxs-lookup"><span data-stu-id="ef180-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef180-143">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ef180-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="ef180-144">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="ef180-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef180-145">備註</span><span class="sxs-lookup"><span data-stu-id="ef180-145">Remarks</span></span>  
 <span data-ttu-id="ef180-146">如果服務使用的繫結中沒有任何一個是針對使用者名稱/密碼驗證設定的，就會忽略這個項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="ef180-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="ef180-147">其中包括 `customUserNamePasswordValidatorType`、`includeWindowsGroups`、`membershipProviderName` 和 `userNamePasswordValidationMode`。</span><span class="sxs-lookup"><span data-stu-id="ef180-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="ef180-148">如果服務使用的繫結中沒有任何一個是設定成針對使用者名稱/密碼使用 Windows 驗證，就會忽略與登錄權杖快取相關的設定。</span><span class="sxs-lookup"><span data-stu-id="ef180-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="ef180-149">其中包括 `cacheLogonTokenLifetime`、`cacheLogonTokens` 和 `maxCacheLogonTokens`。</span><span class="sxs-lookup"><span data-stu-id="ef180-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef180-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef180-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
