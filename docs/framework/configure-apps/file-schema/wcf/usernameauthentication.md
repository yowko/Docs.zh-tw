---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399193"
---
# \<userNameAuthentication>
<span data-ttu-id="b0e45-101">根據使用者名稱和密碼來指定服務的認證。</span><span class="sxs-lookup"><span data-stu-id="b0e45-101">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="b0e45-102">語法</span><span class="sxs-lookup"><span data-stu-id="b0e45-102">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0e45-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b0e45-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b0e45-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b0e45-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0e45-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b0e45-105">Attributes</span></span>  
  
|<span data-ttu-id="b0e45-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b0e45-106">Attribute</span></span>|<span data-ttu-id="b0e45-107">描述</span><span class="sxs-lookup"><span data-stu-id="b0e45-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="b0e45-108"><xref:System.TimeSpan>，指定快取權杖的最大時間長度。</span><span class="sxs-lookup"><span data-stu-id="b0e45-108">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="b0e45-109">預設為 00:15:00。</span><span class="sxs-lookup"><span data-stu-id="b0e45-109">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="b0e45-110">布林值，指定是否要快取登入權杖。</span><span class="sxs-lookup"><span data-stu-id="b0e45-110">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="b0e45-111">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b0e45-111">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="b0e45-112">字串，指定所使用的自訂使用者名稱密碼驗證程式的型別。</span><span class="sxs-lookup"><span data-stu-id="b0e45-112">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="b0e45-113">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="b0e45-113">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="b0e45-114">布林值，指定 Windows 群組是否包含在安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="b0e45-114">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="b0e45-115">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="b0e45-115">The default is `true`.</span></span><br /><br /> <span data-ttu-id="b0e45-116">將這個屬性設定為 `true` 會有效能方面的影響，因為它會造成完整的群組擴充。</span><span class="sxs-lookup"><span data-stu-id="b0e45-116">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="b0e45-117">如果您不需要建立使用者所屬之群組的清單，請將此屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b0e45-117">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="b0e45-118">整數，指定快取登入權杖的數目上限。</span><span class="sxs-lookup"><span data-stu-id="b0e45-118">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="b0e45-119">這個值應大於零。</span><span class="sxs-lookup"><span data-stu-id="b0e45-119">This value should be larger than zero.</span></span> <span data-ttu-id="b0e45-120">預設值為 128。</span><span class="sxs-lookup"><span data-stu-id="b0e45-120">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="b0e45-121">當繫結的 `clientCredentialType` 屬性設為 `username` 時，使用者名稱會對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="b0e45-121">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="b0e45-122">您可以使用這個屬性來覆寫這個行為，該屬性是一個字串，其中包含 <xref:System.Web.Security.MembershipProvider> 值的名稱，可提供相關的密碼驗證機制。</span><span class="sxs-lookup"><span data-stu-id="b0e45-122">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="b0e45-123">指定驗證使用者名稱密碼的方法。</span><span class="sxs-lookup"><span data-stu-id="b0e45-123">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="b0e45-124">有效值為：</span><span class="sxs-lookup"><span data-stu-id="b0e45-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="b0e45-125">-Windows</span><span class="sxs-lookup"><span data-stu-id="b0e45-125">-   Windows</span></span><br /><span data-ttu-id="b0e45-126">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="b0e45-126">-   MembershipProvider</span></span><br /><span data-ttu-id="b0e45-127">-Custom</span><span class="sxs-lookup"><span data-stu-id="b0e45-127">-   Custom</span></span><br /><br /> <span data-ttu-id="b0e45-128">預設為 Windows。</span><span class="sxs-lookup"><span data-stu-id="b0e45-128">The default is Windows.</span></span> <span data-ttu-id="b0e45-129">此屬性的型別為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>。</span><span class="sxs-lookup"><span data-stu-id="b0e45-129">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0e45-130">子元素</span><span class="sxs-lookup"><span data-stu-id="b0e45-130">Child Elements</span></span>  
 <span data-ttu-id="b0e45-131">無。</span><span class="sxs-lookup"><span data-stu-id="b0e45-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0e45-132">父項目</span><span class="sxs-lookup"><span data-stu-id="b0e45-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b0e45-133">元素</span><span class="sxs-lookup"><span data-stu-id="b0e45-133">Element</span></span>|<span data-ttu-id="b0e45-134">描述</span><span class="sxs-lookup"><span data-stu-id="b0e45-134">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="b0e45-135">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="b0e45-135">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0e45-136">備註</span><span class="sxs-lookup"><span data-stu-id="b0e45-136">Remarks</span></span>  
 <span data-ttu-id="b0e45-137">如果服務使用的繫結中沒有任何一個是針對使用者名稱/密碼驗證設定的，就會忽略這個項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="b0e45-137">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="b0e45-138">其中包括 `customUserNamePasswordValidatorType`、`includeWindowsGroups`、`membershipProviderName` 和 `userNamePasswordValidationMode`。</span><span class="sxs-lookup"><span data-stu-id="b0e45-138">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="b0e45-139">如果服務使用的繫結中沒有任何一個是設定成針對使用者名稱/密碼使用 Windows 驗證，就會忽略與登錄權杖快取相關的設定。</span><span class="sxs-lookup"><span data-stu-id="b0e45-139">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="b0e45-140">其中包括 `cacheLogonTokenLifetime`、`cacheLogonTokens` 和 `maxCacheLogonTokens`。</span><span class="sxs-lookup"><span data-stu-id="b0e45-140">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e45-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0e45-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
