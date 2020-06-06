---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 0983380e553acfe246d6b987784d818b8ae85b17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152576"
---
# \<serviceTokenResolver>
<span data-ttu-id="e3ddc-101">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e3ddc-102">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="e3ddc-103">語法</span><span class="sxs-lookup"><span data-stu-id="e3ddc-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3ddc-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e3ddc-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e3ddc-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3ddc-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e3ddc-106">Attributes</span></span>  
  
|<span data-ttu-id="e3ddc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e3ddc-107">Attribute</span></span>|<span data-ttu-id="e3ddc-108">描述</span><span class="sxs-lookup"><span data-stu-id="e3ddc-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3ddc-109">type</span><span class="sxs-lookup"><span data-stu-id="e3ddc-109">type</span></span>|<span data-ttu-id="e3ddc-110">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="e3ddc-111">可能是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 類型或衍生自類別的類型 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="e3ddc-112">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="e3ddc-113">必要。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3ddc-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e3ddc-114">Child Elements</span></span>  
 <span data-ttu-id="e3ddc-115">無</span><span class="sxs-lookup"><span data-stu-id="e3ddc-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3ddc-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e3ddc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e3ddc-117">元素</span><span class="sxs-lookup"><span data-stu-id="e3ddc-117">Element</span></span>|<span data-ttu-id="e3ddc-118">描述</span><span class="sxs-lookup"><span data-stu-id="e3ddc-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="e3ddc-119">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ddc-120">備註</span><span class="sxs-lookup"><span data-stu-id="e3ddc-120">Remarks</span></span>  
 <span data-ttu-id="e3ddc-121">服務權杖解析程式可以用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e3ddc-122">它是用來抓取用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="e3ddc-123">您必須指定 `type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="e3ddc-124">指定的型別可以是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或衍生自類別的自訂型別 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="e3ddc-125">某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="e3ddc-126">個別權杖處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3ddc-127">將專案指定為專案的 `<serviceTokenResolver>` 子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e3ddc-128">元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="e3ddc-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3ddc-129">範例</span><span class="sxs-lookup"><span data-stu-id="e3ddc-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
