---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255181"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="30015-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="30015-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="30015-102">註冊的連入宣告的宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="30015-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="30015-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="30015-103">\<system.identityModel></span></span>  
<span data-ttu-id="30015-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="30015-104">\<identityConfiguration></span></span>  
<span data-ttu-id="30015-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="30015-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30015-106">語法</span><span class="sxs-lookup"><span data-stu-id="30015-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30015-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30015-107">Attributes and Elements</span></span>  
 <span data-ttu-id="30015-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="30015-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30015-109">屬性</span><span class="sxs-lookup"><span data-stu-id="30015-109">Attributes</span></span>  
  
|<span data-ttu-id="30015-110">屬性</span><span class="sxs-lookup"><span data-stu-id="30015-110">Attribute</span></span>|<span data-ttu-id="30015-111">描述</span><span class="sxs-lookup"><span data-stu-id="30015-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30015-112">類型</span><span class="sxs-lookup"><span data-stu-id="30015-112">type</span></span>|<span data-ttu-id="30015-113">指定自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別。</span><span class="sxs-lookup"><span data-stu-id="30015-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="30015-114">如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="30015-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30015-115">子元素</span><span class="sxs-lookup"><span data-stu-id="30015-115">Child Elements</span></span>  
 <span data-ttu-id="30015-116">如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthenticationManager>`項目不會子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>可以定義子組態項目。</span><span class="sxs-lookup"><span data-stu-id="30015-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30015-117">父項目</span><span class="sxs-lookup"><span data-stu-id="30015-117">Parent Elements</span></span>  
  
|<span data-ttu-id="30015-118">項目</span><span class="sxs-lookup"><span data-stu-id="30015-118">Element</span></span>|<span data-ttu-id="30015-119">描述</span><span class="sxs-lookup"><span data-stu-id="30015-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30015-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="30015-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="30015-121">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="30015-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30015-122">備註</span><span class="sxs-lookup"><span data-stu-id="30015-122">Remarks</span></span>  
 <span data-ttu-id="30015-123">透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthenticationManager>類別回應連入宣告。</span><span class="sxs-lookup"><span data-stu-id="30015-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="30015-124">如果沒有`type`指定屬性或如果`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthenticationManager>類別，`<claimsAuthenticationManager>`項目未採用子元素。</span><span class="sxs-lookup"><span data-stu-id="30015-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="30015-125">您可以指定`type`屬性來註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthenticationManager>類別來實作自訂行為。</span><span class="sxs-lookup"><span data-stu-id="30015-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="30015-126">在衍生的類別可支援透過子項目的設定`<claimsAuthenticationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>方法來處理這些項目。</span><span class="sxs-lookup"><span data-stu-id="30015-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="30015-127">子項目定義的結構描述是由設計工具的類別。</span><span class="sxs-lookup"><span data-stu-id="30015-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="30015-128">`<claimsAuthenticationManager>`項目集<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="30015-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30015-129">範例</span><span class="sxs-lookup"><span data-stu-id="30015-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```
