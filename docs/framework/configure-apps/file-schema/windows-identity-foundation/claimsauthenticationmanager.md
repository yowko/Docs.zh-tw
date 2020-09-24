---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 9e099b8de486631702548b8a035a46a7e0f4eb30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158470"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="b01bb-101">為傳入宣告註冊宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="b01bb-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="b01bb-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="b01bb-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b01bb-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b01bb-103">Attributes and Elements</span></span>  

 <span data-ttu-id="b01bb-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b01bb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b01bb-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b01bb-105">Attributes</span></span>  
  
|<span data-ttu-id="b01bb-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b01bb-106">Attribute</span></span>|<span data-ttu-id="b01bb-107">描述</span><span class="sxs-lookup"><span data-stu-id="b01bb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b01bb-108">type</span><span class="sxs-lookup"><span data-stu-id="b01bb-108">type</span></span>|<span data-ttu-id="b01bb-109">指定衍生自類別的自訂型別 <xref:System.Security.Claims.ClaimsAuthenticationManager> 。</span><span class="sxs-lookup"><span data-stu-id="b01bb-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="b01bb-110">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="b01bb-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b01bb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b01bb-111">Child Elements</span></span>  

 <span data-ttu-id="b01bb-112">如果沒有 `type` 屬性（attribute），或 `type` 屬性（attribute）參考類別，專案就不會 <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` 採用子項目; 不過，衍生自的類別 <xref:System.Security.Claims.ClaimsAuthenticationManager> 可以定義子設定元素。</span><span class="sxs-lookup"><span data-stu-id="b01bb-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b01bb-113">父項目</span><span class="sxs-lookup"><span data-stu-id="b01bb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b01bb-114">項目</span><span class="sxs-lookup"><span data-stu-id="b01bb-114">Element</span></span>|<span data-ttu-id="b01bb-115">描述</span><span class="sxs-lookup"><span data-stu-id="b01bb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="b01bb-116">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="b01bb-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b01bb-117">備註</span><span class="sxs-lookup"><span data-stu-id="b01bb-117">Remarks</span></span>  

 <span data-ttu-id="b01bb-118">透過類別提供的預設行為會回應 <xref:System.Security.Claims.ClaimsAuthenticationManager> 傳入宣告。</span><span class="sxs-lookup"><span data-stu-id="b01bb-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="b01bb-119">如果未 `type` 指定屬性 `type` ，或屬性指定 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，則元素不會 `<claimsAuthenticationManager>` 採用子項目。</span><span class="sxs-lookup"><span data-stu-id="b01bb-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="b01bb-120">您可以指定 `type` 屬性來註冊衍生自類別的型別 <xref:System.Security.Claims.ClaimsAuthenticationManager> ，以執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="b01bb-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="b01bb-121">衍生的類別可以藉 `<claimsAuthenticationManager>` 由覆寫 <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> 方法來處理這些元素，藉以支援透過專案的子項目進行設定。</span><span class="sxs-lookup"><span data-stu-id="b01bb-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="b01bb-122">為子專案定義的架構是由類別的設計工具所組成。</span><span class="sxs-lookup"><span data-stu-id="b01bb-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="b01bb-123">`<claimsAuthenticationManager>`元素會設定 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b01bb-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b01bb-124">範例</span><span class="sxs-lookup"><span data-stu-id="b01bb-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
