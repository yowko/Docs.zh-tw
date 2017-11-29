---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 48e5be23b196a24a9d3e2a1dc4639d8ca9823660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="3bd4e-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="3bd4e-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="3bd4e-103">註冊的連入宣告的宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="3bd4e-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="3bd4e-104">\<system.identityModel></span></span>  
<span data-ttu-id="3bd4e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3bd4e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3bd4e-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="3bd4e-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd4e-107">語法</span><span class="sxs-lookup"><span data-stu-id="3bd4e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bd4e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3bd4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3bd4e-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bd4e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3bd4e-110">Attributes</span></span>  
  
|<span data-ttu-id="3bd4e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3bd4e-111">Attribute</span></span>|<span data-ttu-id="3bd4e-112">描述</span><span class="sxs-lookup"><span data-stu-id="3bd4e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bd4e-113">類型</span><span class="sxs-lookup"><span data-stu-id="3bd4e-113">type</span></span>|<span data-ttu-id="3bd4e-114">指定自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="3bd4e-115">如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bd4e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="3bd4e-116">Child Elements</span></span>  
 <span data-ttu-id="3bd4e-117">如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthenticationManager>`項目不接受子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>可以定義子組態項目。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bd4e-118">父項目</span><span class="sxs-lookup"><span data-stu-id="3bd4e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3bd4e-119">項目</span><span class="sxs-lookup"><span data-stu-id="3bd4e-119">Element</span></span>|<span data-ttu-id="3bd4e-120">說明</span><span class="sxs-lookup"><span data-stu-id="3bd4e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bd4e-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3bd4e-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="3bd4e-122">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bd4e-123">備註</span><span class="sxs-lookup"><span data-stu-id="3bd4e-123">Remarks</span></span>  
 <span data-ttu-id="3bd4e-124">透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthenticationManager>類別回應連入宣告。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="3bd4e-125">如果沒有`type`指定屬性或`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthenticationManager>類別，`<claimsAuthenticationManager>`項目不接受子項目。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="3bd4e-126">您可以指定`type`屬性註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別來實作自訂行為。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="3bd4e-127">在衍生的類別可以支援透過子項目的組態`<claimsAuthenticationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>方法來處理這些項目。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="3bd4e-128">子項目定義的結構描述是由類別的設計工具。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="3bd4e-129">`<claimsAuthenticationManager>`項目集合<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="3bd4e-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bd4e-130">範例</span><span class="sxs-lookup"><span data-stu-id="3bd4e-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
