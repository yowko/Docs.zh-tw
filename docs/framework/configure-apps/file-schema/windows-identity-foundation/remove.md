---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251919"
---
# <a name="remove"></a><span data-ttu-id="229ca-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="229ca-101">\<remove></span></span>
<span data-ttu-id="229ca-102">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="229ca-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="229ca-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="229ca-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="229ca-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="229ca-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="229ca-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="229ca-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="229ca-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="229ca-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="229ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="229ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229ca-108">語法</span><span class="sxs-lookup"><span data-stu-id="229ca-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="229ca-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="229ca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="229ca-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="229ca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="229ca-111">屬性</span><span class="sxs-lookup"><span data-stu-id="229ca-111">Attributes</span></span>  
  
|<span data-ttu-id="229ca-112">屬性</span><span class="sxs-lookup"><span data-stu-id="229ca-112">Attribute</span></span>|<span data-ttu-id="229ca-113">說明</span><span class="sxs-lookup"><span data-stu-id="229ca-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="229ca-114">型別</span><span class="sxs-lookup"><span data-stu-id="229ca-114">type</span></span>|<span data-ttu-id="229ca-115">要移除之權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="229ca-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="229ca-116">如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="229ca-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="229ca-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="229ca-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="229ca-118">子元素</span><span class="sxs-lookup"><span data-stu-id="229ca-118">Child Elements</span></span>  
 <span data-ttu-id="229ca-119">無</span><span class="sxs-lookup"><span data-stu-id="229ca-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="229ca-120">父項目</span><span class="sxs-lookup"><span data-stu-id="229ca-120">Parent Elements</span></span>  
  
|<span data-ttu-id="229ca-121">項目</span><span class="sxs-lookup"><span data-stu-id="229ca-121">Element</span></span>|<span data-ttu-id="229ca-122">描述</span><span class="sxs-lookup"><span data-stu-id="229ca-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="229ca-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="229ca-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="229ca-124">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="229ca-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="229ca-125">範例</span><span class="sxs-lookup"><span data-stu-id="229ca-125">Example</span></span>  
 <span data-ttu-id="229ca-126">下列 XML 顯示如何使用`<add>`和`<remove>`專案, 以自訂會話權杖處理常式取代預設會話權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="229ca-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="229ca-127">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="229ca-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
