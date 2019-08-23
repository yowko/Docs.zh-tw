---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 69d34cb54c2236f178ac4291ed24a3f5b45db48e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923101"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="d3cad-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="d3cad-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="d3cad-102">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="d3cad-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="d3cad-103">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="d3cad-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="d3cad-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d3cad-104">\<system.identityModel></span></span>  
<span data-ttu-id="d3cad-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d3cad-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d3cad-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d3cad-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d3cad-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d3cad-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="d3cad-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="d3cad-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3cad-109">語法</span><span class="sxs-lookup"><span data-stu-id="d3cad-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3cad-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3cad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3cad-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d3cad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3cad-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d3cad-112">Attributes</span></span>  
  
|<span data-ttu-id="d3cad-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d3cad-113">Attribute</span></span>|<span data-ttu-id="d3cad-114">描述</span><span class="sxs-lookup"><span data-stu-id="d3cad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3cad-115">型別</span><span class="sxs-lookup"><span data-stu-id="d3cad-115">type</span></span>|<span data-ttu-id="d3cad-116">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="d3cad-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="d3cad-117"><xref:System.IdentityModel.Selectors.SecurityTokenResolver>可能是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類別的類型。</span><span class="sxs-lookup"><span data-stu-id="d3cad-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="d3cad-118">如需如何指定屬性的`type`詳細資訊, 請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="d3cad-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="d3cad-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="d3cad-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3cad-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d3cad-120">Child Elements</span></span>  
 <span data-ttu-id="d3cad-121">None</span><span class="sxs-lookup"><span data-stu-id="d3cad-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3cad-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d3cad-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d3cad-123">項目</span><span class="sxs-lookup"><span data-stu-id="d3cad-123">Element</span></span>|<span data-ttu-id="d3cad-124">描述</span><span class="sxs-lookup"><span data-stu-id="d3cad-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3cad-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d3cad-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="d3cad-126">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="d3cad-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3cad-127">備註</span><span class="sxs-lookup"><span data-stu-id="d3cad-127">Remarks</span></span>  
 <span data-ttu-id="d3cad-128">服務權杖解析程式可以用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="d3cad-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="d3cad-129">它是用來抓取用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3cad-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="d3cad-130">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="d3cad-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="d3cad-131">指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或衍生<xref:System.IdentityModel.Selectors.SecurityTokenResolver>自類別的自訂型別。</span><span class="sxs-lookup"><span data-stu-id="d3cad-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="d3cad-132">某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="d3cad-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="d3cad-133">個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="d3cad-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3cad-134">將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代, 但仍支援回溯相容性。 `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="d3cad-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="d3cad-135">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="d3cad-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3cad-136">範例</span><span class="sxs-lookup"><span data-stu-id="d3cad-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
