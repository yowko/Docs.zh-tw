---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 30a53c11b551623311f7ca3f957143fc702568a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251842"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="b9784-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="b9784-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="b9784-102">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="b9784-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b9784-103">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="b9784-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="b9784-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b9784-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b9784-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b9784-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b9784-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b9784-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b9784-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b9784-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b9784-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b9784-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="b9784-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="b9784-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9784-110">語法</span><span class="sxs-lookup"><span data-stu-id="b9784-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9784-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b9784-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b9784-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b9784-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9784-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b9784-113">Attributes</span></span>  
  
|<span data-ttu-id="b9784-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b9784-114">Attribute</span></span>|<span data-ttu-id="b9784-115">描述</span><span class="sxs-lookup"><span data-stu-id="b9784-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9784-116">型別</span><span class="sxs-lookup"><span data-stu-id="b9784-116">type</span></span>|<span data-ttu-id="b9784-117">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="b9784-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="b9784-118"><xref:System.IdentityModel.Selectors.SecurityTokenResolver>可能是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>類型或衍生自類別的類型。</span><span class="sxs-lookup"><span data-stu-id="b9784-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="b9784-119">如需如何指定屬性的`type`詳細資訊，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="b9784-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="b9784-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="b9784-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9784-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b9784-121">Child Elements</span></span>  
 <span data-ttu-id="b9784-122">None</span><span class="sxs-lookup"><span data-stu-id="b9784-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9784-123">父項目</span><span class="sxs-lookup"><span data-stu-id="b9784-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b9784-124">項目</span><span class="sxs-lookup"><span data-stu-id="b9784-124">Element</span></span>|<span data-ttu-id="b9784-125">說明</span><span class="sxs-lookup"><span data-stu-id="b9784-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9784-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b9784-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b9784-127">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="b9784-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9784-128">備註</span><span class="sxs-lookup"><span data-stu-id="b9784-128">Remarks</span></span>  
 <span data-ttu-id="b9784-129">服務權杖解析程式可以用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="b9784-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="b9784-130">它是用來抓取用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="b9784-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="b9784-131">您必須指定`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="b9784-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="b9784-132">指定的型別可以是<xref:System.IdentityModel.Selectors.SecurityTokenResolver>或衍生<xref:System.IdentityModel.Selectors.SecurityTokenResolver>自類別的自訂型別。</span><span class="sxs-lookup"><span data-stu-id="b9784-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="b9784-133">某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="b9784-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="b9784-134">個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="b9784-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9784-135">將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代，但仍支援回溯相容性。 `<serviceTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="b9784-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b9784-136">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="b9784-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9784-137">範例</span><span class="sxs-lookup"><span data-stu-id="b9784-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
 