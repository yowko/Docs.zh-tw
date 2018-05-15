---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="f7efc-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="f7efc-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="f7efc-103">註冊由權杖處理常式集合中的處理常式的服務權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="f7efc-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f7efc-104">服務語彙基元解析程式用來解析連入權杖和訊息上的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f7efc-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="f7efc-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f7efc-105">\<system.identityModel></span></span>  
<span data-ttu-id="f7efc-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f7efc-106">\<identityConfiguration></span></span>  
<span data-ttu-id="f7efc-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f7efc-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f7efc-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f7efc-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="f7efc-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="f7efc-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7efc-110">語法</span><span class="sxs-lookup"><span data-stu-id="f7efc-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7efc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7efc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f7efc-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f7efc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7efc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f7efc-113">Attributes</span></span>  
  
|<span data-ttu-id="f7efc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f7efc-114">Attribute</span></span>|<span data-ttu-id="f7efc-115">描述</span><span class="sxs-lookup"><span data-stu-id="f7efc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7efc-116">類型</span><span class="sxs-lookup"><span data-stu-id="f7efc-116">type</span></span>|<span data-ttu-id="f7efc-117">指定的服務權杖解析程式類型。</span><span class="sxs-lookup"><span data-stu-id="f7efc-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="f7efc-118">任一<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類型<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="f7efc-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="f7efc-119">如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="f7efc-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="f7efc-120">必要。</span><span class="sxs-lookup"><span data-stu-id="f7efc-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7efc-121">子項目</span><span class="sxs-lookup"><span data-stu-id="f7efc-121">Child Elements</span></span>  
 <span data-ttu-id="f7efc-122">無</span><span class="sxs-lookup"><span data-stu-id="f7efc-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7efc-123">父項目</span><span class="sxs-lookup"><span data-stu-id="f7efc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f7efc-124">項目</span><span class="sxs-lookup"><span data-stu-id="f7efc-124">Element</span></span>|<span data-ttu-id="f7efc-125">描述</span><span class="sxs-lookup"><span data-stu-id="f7efc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7efc-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f7efc-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="f7efc-127">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="f7efc-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7efc-128">備註</span><span class="sxs-lookup"><span data-stu-id="f7efc-128">Remarks</span></span>  
 <span data-ttu-id="f7efc-129">服務語彙基元解析程式可以用來解析連入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="f7efc-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="f7efc-130">它用來擷取應該用來將傳入的權杖解密的金鑰。</span><span class="sxs-lookup"><span data-stu-id="f7efc-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="f7efc-131">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="f7efc-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="f7efc-132">指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或自訂型別衍生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="f7efc-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="f7efc-133">某些權杖處理常式可讓您在組態中指定服務語彙基元解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="f7efc-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="f7efc-134">在個別的語彙基元處理常式上的設定會覆寫安全性權杖處理常式集合上指定。</span><span class="sxs-lookup"><span data-stu-id="f7efc-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7efc-135">指定`<serviceTokenResolver>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="f7efc-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="f7efc-136">設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="f7efc-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7efc-137">範例</span><span class="sxs-lookup"><span data-stu-id="f7efc-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
