---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347499"
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="fd488-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="fd488-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="fd488-103">註冊的服務權杖解析程式由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="fd488-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="fd488-104">服務權杖解析程式用來解析上傳入的權杖和訊息的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fd488-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="fd488-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fd488-105">\<system.identityModel></span></span>  
<span data-ttu-id="fd488-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fd488-106">\<identityConfiguration></span></span>  
<span data-ttu-id="fd488-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fd488-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fd488-108">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="fd488-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="fd488-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="fd488-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd488-110">語法</span><span class="sxs-lookup"><span data-stu-id="fd488-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd488-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd488-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fd488-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fd488-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd488-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fd488-113">Attributes</span></span>  
  
|<span data-ttu-id="fd488-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fd488-114">Attribute</span></span>|<span data-ttu-id="fd488-115">描述</span><span class="sxs-lookup"><span data-stu-id="fd488-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd488-116">類型</span><span class="sxs-lookup"><span data-stu-id="fd488-116">type</span></span>|<span data-ttu-id="fd488-117">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="fd488-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="fd488-118">任一<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類型<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="fd488-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="fd488-119">如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="fd488-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="fd488-120">必要。</span><span class="sxs-lookup"><span data-stu-id="fd488-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd488-121">子元素</span><span class="sxs-lookup"><span data-stu-id="fd488-121">Child Elements</span></span>  
 <span data-ttu-id="fd488-122">無</span><span class="sxs-lookup"><span data-stu-id="fd488-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd488-123">父項目</span><span class="sxs-lookup"><span data-stu-id="fd488-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fd488-124">項目</span><span class="sxs-lookup"><span data-stu-id="fd488-124">Element</span></span>|<span data-ttu-id="fd488-125">描述</span><span class="sxs-lookup"><span data-stu-id="fd488-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd488-126">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="fd488-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="fd488-127">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="fd488-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd488-128">備註</span><span class="sxs-lookup"><span data-stu-id="fd488-128">Remarks</span></span>  
 <span data-ttu-id="fd488-129">若要解決上傳入的權杖和訊息的加密語彙基元可用服務權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="fd488-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="fd488-130">它用來擷取應該用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="fd488-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="fd488-131">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="fd488-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="fd488-132">指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="fd488-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="fd488-133">某些權杖處理常式可讓您在組態中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="fd488-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="fd488-134">在個別的權杖處理常式上的設定會覆寫所指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="fd488-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd488-135">指定`<serviceTokenResolver>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="fd488-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fd488-136">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="fd488-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd488-137">範例</span><span class="sxs-lookup"><span data-stu-id="fd488-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
