---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941821"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="341da-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="341da-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="341da-102">為傳入宣告註冊宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="341da-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="341da-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="341da-103">\<system.identityModel></span></span>  
<span data-ttu-id="341da-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="341da-104">\<identityConfiguration></span></span>  
<span data-ttu-id="341da-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="341da-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="341da-106">語法</span><span class="sxs-lookup"><span data-stu-id="341da-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="341da-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="341da-107">Attributes and Elements</span></span>  
 <span data-ttu-id="341da-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="341da-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="341da-109">屬性</span><span class="sxs-lookup"><span data-stu-id="341da-109">Attributes</span></span>  
  
|<span data-ttu-id="341da-110">屬性</span><span class="sxs-lookup"><span data-stu-id="341da-110">Attribute</span></span>|<span data-ttu-id="341da-111">說明</span><span class="sxs-lookup"><span data-stu-id="341da-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="341da-112">型別</span><span class="sxs-lookup"><span data-stu-id="341da-112">type</span></span>|<span data-ttu-id="341da-113">指定衍生<xref:System.Security.Claims.ClaimsAuthenticationManager>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="341da-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="341da-114">如需如何指定屬性的`type`詳細資訊, 請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="341da-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="341da-115">子元素</span><span class="sxs-lookup"><span data-stu-id="341da-115">Child Elements</span></span>  
 <span data-ttu-id="341da-116"><xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager>如果沒有`type`屬性, 或屬性參考類別, 則專案不會採用子項目; 不過, 衍生自的類別可以定義子設定元素。 `type`</span><span class="sxs-lookup"><span data-stu-id="341da-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="341da-117">父項目</span><span class="sxs-lookup"><span data-stu-id="341da-117">Parent Elements</span></span>  
  
|<span data-ttu-id="341da-118">項目</span><span class="sxs-lookup"><span data-stu-id="341da-118">Element</span></span>|<span data-ttu-id="341da-119">描述</span><span class="sxs-lookup"><span data-stu-id="341da-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="341da-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="341da-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="341da-121">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="341da-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="341da-122">備註</span><span class="sxs-lookup"><span data-stu-id="341da-122">Remarks</span></span>  
 <span data-ttu-id="341da-123">透過<xref:System.Security.Claims.ClaimsAuthenticationManager>類別提供的預設行為會回顯傳入宣告。</span><span class="sxs-lookup"><span data-stu-id="341da-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="341da-124">如果未`type`指定任何屬性, 或`type`屬性指定了<xref:System.Security.Claims.ClaimsAuthenticationManager>類別, 則`<claimsAuthenticationManager>`專案不會採用子項目。</span><span class="sxs-lookup"><span data-stu-id="341da-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="341da-125">您可以指定`type`屬性來註冊衍生自類別的<xref:System.Security.Claims.ClaimsAuthenticationManager>型別, 以執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="341da-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="341da-126">衍生類別可以藉由覆`<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>寫方法來處理這些專案, 藉以支援透過專案的子專案進行設定。</span><span class="sxs-lookup"><span data-stu-id="341da-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="341da-127">為子專案定義的架構是由類別的設計工具所組成。</span><span class="sxs-lookup"><span data-stu-id="341da-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="341da-128">`<claimsAuthenticationManager>`元素會<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>設定屬性。</span><span class="sxs-lookup"><span data-stu-id="341da-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="341da-129">範例</span><span class="sxs-lookup"><span data-stu-id="341da-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
