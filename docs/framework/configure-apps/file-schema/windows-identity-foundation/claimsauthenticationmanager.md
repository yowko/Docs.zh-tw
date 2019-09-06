---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252096"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="d8099-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="d8099-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="d8099-102">為傳入宣告註冊宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="d8099-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="d8099-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d8099-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d8099-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d8099-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d8099-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d8099-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d8099-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="d8099-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8099-107">語法</span><span class="sxs-lookup"><span data-stu-id="d8099-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8099-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8099-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8099-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8099-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8099-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d8099-110">Attributes</span></span>  
  
|<span data-ttu-id="d8099-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d8099-111">Attribute</span></span>|<span data-ttu-id="d8099-112">描述</span><span class="sxs-lookup"><span data-stu-id="d8099-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8099-113">型別</span><span class="sxs-lookup"><span data-stu-id="d8099-113">type</span></span>|<span data-ttu-id="d8099-114">指定衍生<xref:System.Security.Claims.ClaimsAuthenticationManager>自類別的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="d8099-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="d8099-115">如需如何指定屬性的`type`詳細資訊，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="d8099-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8099-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d8099-116">Child Elements</span></span>  
 <span data-ttu-id="d8099-117"><xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager>如果沒有`type`屬性，或屬性參考類別，則專案不會採用子項目; 不過，衍生自的類別可以定義子設定元素。 `type`</span><span class="sxs-lookup"><span data-stu-id="d8099-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8099-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d8099-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d8099-119">項目</span><span class="sxs-lookup"><span data-stu-id="d8099-119">Element</span></span>|<span data-ttu-id="d8099-120">描述</span><span class="sxs-lookup"><span data-stu-id="d8099-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8099-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8099-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d8099-122">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="d8099-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8099-123">備註</span><span class="sxs-lookup"><span data-stu-id="d8099-123">Remarks</span></span>  
 <span data-ttu-id="d8099-124">透過<xref:System.Security.Claims.ClaimsAuthenticationManager>類別提供的預設行為會回顯傳入宣告。</span><span class="sxs-lookup"><span data-stu-id="d8099-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="d8099-125">如果未`type`指定任何屬性，或`type`屬性指定了<xref:System.Security.Claims.ClaimsAuthenticationManager>類別，則`<claimsAuthenticationManager>`專案不會採用子項目。</span><span class="sxs-lookup"><span data-stu-id="d8099-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="d8099-126">您可以指定`type`屬性來註冊衍生自類別的<xref:System.Security.Claims.ClaimsAuthenticationManager>型別，以執行自訂行為。</span><span class="sxs-lookup"><span data-stu-id="d8099-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="d8099-127">衍生類別可以藉由覆`<claimsAuthenticationManager>` <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>寫方法來處理這些專案，藉以支援透過專案的子專案進行設定。</span><span class="sxs-lookup"><span data-stu-id="d8099-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="d8099-128">為子專案定義的架構是由類別的設計工具所組成。</span><span class="sxs-lookup"><span data-stu-id="d8099-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="d8099-129">`<claimsAuthenticationManager>`元素會<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>設定屬性。</span><span class="sxs-lookup"><span data-stu-id="d8099-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8099-130">範例</span><span class="sxs-lookup"><span data-stu-id="d8099-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
