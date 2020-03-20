---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152745"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="5bb90-101">\<聲明身份驗證管理器></span><span class="sxs-lookup"><span data-stu-id="5bb90-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="5bb90-102">註冊傳入聲明的聲明身份驗證管理器。</span><span class="sxs-lookup"><span data-stu-id="5bb90-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="5bb90-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5bb90-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bb90-104">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5bb90-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5bb90-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5bb90-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5bb90-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<聲明身份驗證管理器>**</span><span class="sxs-lookup"><span data-stu-id="5bb90-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bb90-107">語法</span><span class="sxs-lookup"><span data-stu-id="5bb90-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bb90-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5bb90-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5bb90-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5bb90-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bb90-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5bb90-110">Attributes</span></span>  
  
|<span data-ttu-id="5bb90-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5bb90-111">Attribute</span></span>|<span data-ttu-id="5bb90-112">描述</span><span class="sxs-lookup"><span data-stu-id="5bb90-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bb90-113">type</span><span class="sxs-lookup"><span data-stu-id="5bb90-113">type</span></span>|<span data-ttu-id="5bb90-114">指定派生自類的<xref:System.Security.Claims.ClaimsAuthenticationManager>自訂類型。</span><span class="sxs-lookup"><span data-stu-id="5bb90-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="5bb90-115">有關如何指定屬性的詳細資訊，`type`請參閱 [自訂類型引用]。</span><span class="sxs-lookup"><span data-stu-id="5bb90-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bb90-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5bb90-116">Child Elements</span></span>  
 <span data-ttu-id="5bb90-117">如果沒有`type`屬性，或者該`type`屬性引用該<xref:System.Security.Claims.ClaimsAuthenticationManager>類，則`<claimsAuthenticationManager>`元素不會採用子項目;如果該屬性引用該類，則元素不會採用子項目。但是，派生自的<xref:System.Security.Claims.ClaimsAuthenticationManager>類可以定義子配置元素。</span><span class="sxs-lookup"><span data-stu-id="5bb90-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bb90-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5bb90-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5bb90-119">元素</span><span class="sxs-lookup"><span data-stu-id="5bb90-119">Element</span></span>|<span data-ttu-id="5bb90-120">描述</span><span class="sxs-lookup"><span data-stu-id="5bb90-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bb90-121">\<身份配置></span><span class="sxs-lookup"><span data-stu-id="5bb90-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="5bb90-122">指定服務等級標識設置。</span><span class="sxs-lookup"><span data-stu-id="5bb90-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bb90-123">備註</span><span class="sxs-lookup"><span data-stu-id="5bb90-123">Remarks</span></span>  
 <span data-ttu-id="5bb90-124">通過<xref:System.Security.Claims.ClaimsAuthenticationManager>類提供的預設行為與傳入的聲明相呼應。</span><span class="sxs-lookup"><span data-stu-id="5bb90-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="5bb90-125">如果未`type`指定屬性或`type`屬性指定類，<xref:System.Security.Claims.ClaimsAuthenticationManager>則`<claimsAuthenticationManager>`元素不會採用子項目。</span><span class="sxs-lookup"><span data-stu-id="5bb90-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="5bb90-126">可以指定屬性`type`以註冊從<xref:System.Security.Claims.ClaimsAuthenticationManager>類派生的類型以實現自訂行為。</span><span class="sxs-lookup"><span data-stu-id="5bb90-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="5bb90-127">派生類可以通過重寫`<claimsAuthenticationManager>`<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>處理這些元素的方法來支援通過元素的子項目進行配置。</span><span class="sxs-lookup"><span data-stu-id="5bb90-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="5bb90-128">為子項目定義的架構由類的設計器決定。</span><span class="sxs-lookup"><span data-stu-id="5bb90-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="5bb90-129">元素`<claimsAuthenticationManager>`設置<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="5bb90-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bb90-130">範例</span><span class="sxs-lookup"><span data-stu-id="5bb90-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
