---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 3ea9684245bd1c1c3b9ce171a045fff49d0ba592
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156910"
---
# \<serviceTokenResolver>

<span data-ttu-id="9e4b8-101">註冊權杖處理常式集合中處理常式所使用的服務權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-101">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="9e4b8-102">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-102">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="9e4b8-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e4b8-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e4b8-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9e4b8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9e4b8-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e4b8-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9e4b8-106">Attributes</span></span>  
  
|<span data-ttu-id="9e4b8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9e4b8-107">Attribute</span></span>|<span data-ttu-id="9e4b8-108">描述</span><span class="sxs-lookup"><span data-stu-id="9e4b8-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e4b8-109">type</span><span class="sxs-lookup"><span data-stu-id="9e4b8-109">type</span></span>|<span data-ttu-id="9e4b8-110">指定服務權杖解析程式的類型。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-110">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="9e4b8-111">型別 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或衍生自類別的型別 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-111">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="9e4b8-112">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-112">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="9e4b8-113">必要。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e4b8-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9e4b8-114">Child Elements</span></span>  

 <span data-ttu-id="9e4b8-115">無</span><span class="sxs-lookup"><span data-stu-id="9e4b8-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e4b8-116">父項目</span><span class="sxs-lookup"><span data-stu-id="9e4b8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="9e4b8-117">項目</span><span class="sxs-lookup"><span data-stu-id="9e4b8-117">Element</span></span>|<span data-ttu-id="9e4b8-118">描述</span><span class="sxs-lookup"><span data-stu-id="9e4b8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="9e4b8-119">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e4b8-120">備註</span><span class="sxs-lookup"><span data-stu-id="9e4b8-120">Remarks</span></span>  

 <span data-ttu-id="9e4b8-121">您可以使用服務權杖解析程式來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-121">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="9e4b8-122">它是用來取出用來解密傳入權杖的金鑰。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-122">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="9e4b8-123">您必須指定 `type` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="9e4b8-124">指定的型別可以是 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 或衍生自類別的自訂型別 <xref:System.IdentityModel.Selectors.SecurityTokenResolver> 。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-124">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="9e4b8-125">某些權杖處理常式可讓您在設定中指定服務權杖解析程式設定。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-125">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="9e4b8-126">個別標記處理常式上的設定會覆寫安全性權杖處理常式集合上指定的設定。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e4b8-127">將 `<serviceTokenResolver>` 元素指定為專案的子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-127">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="9e4b8-128">元素上的設定會覆 `<securityTokenHandlerConfiguration>` 寫元素上的設定 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="9e4b8-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e4b8-129">範例</span><span class="sxs-lookup"><span data-stu-id="9e4b8-129">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
