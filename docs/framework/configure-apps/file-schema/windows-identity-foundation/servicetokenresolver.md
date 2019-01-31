---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267426"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="8b364-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="8b364-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="8b364-102">註冊的服務權杖解析程式由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="8b364-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="8b364-103">服務權杖解析程式用來解析上傳入的權杖和訊息的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8b364-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="8b364-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8b364-104">\<system.identityModel></span></span>  
<span data-ttu-id="8b364-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b364-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8b364-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8b364-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8b364-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b364-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="8b364-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="8b364-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b364-109">語法</span><span class="sxs-lookup"><span data-stu-id="8b364-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b364-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b364-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8b364-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8b364-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b364-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8b364-112">Attributes</span></span>  
  
|<span data-ttu-id="8b364-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8b364-113">Attribute</span></span>|<span data-ttu-id="8b364-114">描述</span><span class="sxs-lookup"><span data-stu-id="8b364-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b364-115">類型</span><span class="sxs-lookup"><span data-stu-id="8b364-115">type</span></span>|<span data-ttu-id="8b364-116">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="8b364-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="8b364-117">任一<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類型<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="8b364-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="8b364-118">如需有關如何指定`type`屬性，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="8b364-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="8b364-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="8b364-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b364-120">子元素</span><span class="sxs-lookup"><span data-stu-id="8b364-120">Child Elements</span></span>  
 <span data-ttu-id="8b364-121">無</span><span class="sxs-lookup"><span data-stu-id="8b364-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b364-122">父項目</span><span class="sxs-lookup"><span data-stu-id="8b364-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8b364-123">項目</span><span class="sxs-lookup"><span data-stu-id="8b364-123">Element</span></span>|<span data-ttu-id="8b364-124">描述</span><span class="sxs-lookup"><span data-stu-id="8b364-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b364-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b364-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="8b364-126">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="8b364-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b364-127">備註</span><span class="sxs-lookup"><span data-stu-id="8b364-127">Remarks</span></span>  
 <span data-ttu-id="8b364-128">若要解決上傳入的權杖和訊息的加密語彙基元可用服務權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="8b364-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="8b364-129">它用來擷取應該用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="8b364-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="8b364-130">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="8b364-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="8b364-131">指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或自訂的型別衍生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類別。</span><span class="sxs-lookup"><span data-stu-id="8b364-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="8b364-132">某些權杖處理常式可讓您在組態中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="8b364-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="8b364-133">在個別的權杖處理常式上的設定會覆寫所指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="8b364-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b364-134">指定`<serviceTokenResolver>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="8b364-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8b364-135">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="8b364-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b364-136">範例</span><span class="sxs-lookup"><span data-stu-id="8b364-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
