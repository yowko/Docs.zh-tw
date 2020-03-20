---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152576"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="2a26a-101">\<服務權杖解析器></span><span class="sxs-lookup"><span data-stu-id="2a26a-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="2a26a-102">註冊權杖處理常式集合中處理常式使用的服務權杖解析器。</span><span class="sxs-lookup"><span data-stu-id="2a26a-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="2a26a-103">服務權杖解析器用於解析傳入權杖和消息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="2a26a-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="2a26a-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a26a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a26a-105">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a26a-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2a26a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2a26a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2a26a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2a26a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2a26a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式配置>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2a26a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="2a26a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<服務權杖解析器>**</span><span class="sxs-lookup"><span data-stu-id="2a26a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a26a-110">語法</span><span class="sxs-lookup"><span data-stu-id="2a26a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a26a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a26a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2a26a-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2a26a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a26a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2a26a-113">Attributes</span></span>  
  
|<span data-ttu-id="2a26a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2a26a-114">Attribute</span></span>|<span data-ttu-id="2a26a-115">描述</span><span class="sxs-lookup"><span data-stu-id="2a26a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a26a-116">type</span><span class="sxs-lookup"><span data-stu-id="2a26a-116">type</span></span>|<span data-ttu-id="2a26a-117">指定服務權杖解析器的類型。</span><span class="sxs-lookup"><span data-stu-id="2a26a-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="2a26a-118">派生自<xref:System.IdentityModel.Selectors.SecurityTokenResolver><xref:System.IdentityModel.Selectors.SecurityTokenResolver>類的類型或類型。</span><span class="sxs-lookup"><span data-stu-id="2a26a-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="2a26a-119">有關如何指定屬性的詳細資訊，`type`請參閱 [自訂類型引用]。</span><span class="sxs-lookup"><span data-stu-id="2a26a-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="2a26a-120">必要。</span><span class="sxs-lookup"><span data-stu-id="2a26a-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a26a-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2a26a-121">Child Elements</span></span>  
 <span data-ttu-id="2a26a-122">None</span><span class="sxs-lookup"><span data-stu-id="2a26a-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a26a-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2a26a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2a26a-124">元素</span><span class="sxs-lookup"><span data-stu-id="2a26a-124">Element</span></span>|<span data-ttu-id="2a26a-125">描述</span><span class="sxs-lookup"><span data-stu-id="2a26a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a26a-126">\<安全權杖處理常式配置></span><span class="sxs-lookup"><span data-stu-id="2a26a-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="2a26a-127">為安全權杖處理常式的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="2a26a-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a26a-128">備註</span><span class="sxs-lookup"><span data-stu-id="2a26a-128">Remarks</span></span>  
 <span data-ttu-id="2a26a-129">服務權杖解析器可用於解析傳入權杖和消息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="2a26a-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="2a26a-130">它用於檢索應用於解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="2a26a-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="2a26a-131">必須指定該`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="2a26a-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="2a26a-132">指定的類型可以是 或<xref:System.IdentityModel.Selectors.SecurityTokenResolver>派生自類的<xref:System.IdentityModel.Selectors.SecurityTokenResolver>自訂類型。</span><span class="sxs-lookup"><span data-stu-id="2a26a-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="2a26a-133">某些權杖處理常式允許您在配置中指定服務權杖解析器設置。</span><span class="sxs-lookup"><span data-stu-id="2a26a-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="2a26a-134">各個權杖處理常式上的設置將覆蓋在安全權杖處理常式集合上指定的設置。</span><span class="sxs-lookup"><span data-stu-id="2a26a-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a26a-135">將`<serviceTokenResolver>`元素指定為[\<標識配置>](identityconfiguration.md)元素的子項目已被棄用，但仍支援向後相容性。</span><span class="sxs-lookup"><span data-stu-id="2a26a-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="2a26a-136">元素上的`<securityTokenHandlerConfiguration>`設置將覆蓋元素上的`<identityConfiguration>`設置。</span><span class="sxs-lookup"><span data-stu-id="2a26a-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a26a-137">範例</span><span class="sxs-lookup"><span data-stu-id="2a26a-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
