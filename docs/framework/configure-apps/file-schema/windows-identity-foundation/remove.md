---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251919"
---
# \<remove>
<span data-ttu-id="cb0a6-101">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="cb0a6-102">語法</span><span class="sxs-lookup"><span data-stu-id="cb0a6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb0a6-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cb0a6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cb0a6-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb0a6-105">屬性</span><span class="sxs-lookup"><span data-stu-id="cb0a6-105">Attributes</span></span>  
  
|<span data-ttu-id="cb0a6-106">屬性</span><span class="sxs-lookup"><span data-stu-id="cb0a6-106">Attribute</span></span>|<span data-ttu-id="cb0a6-107">描述</span><span class="sxs-lookup"><span data-stu-id="cb0a6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb0a6-108">type</span><span class="sxs-lookup"><span data-stu-id="cb0a6-108">type</span></span>|<span data-ttu-id="cb0a6-109">要移除之權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="cb0a6-110">如需如何指定屬性的詳細資訊 `type` ，請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="cb0a6-111">必要。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb0a6-112">子元素</span><span class="sxs-lookup"><span data-stu-id="cb0a6-112">Child Elements</span></span>  
 <span data-ttu-id="cb0a6-113">無</span><span class="sxs-lookup"><span data-stu-id="cb0a6-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb0a6-114">父項目</span><span class="sxs-lookup"><span data-stu-id="cb0a6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cb0a6-115">元素</span><span class="sxs-lookup"><span data-stu-id="cb0a6-115">Element</span></span>|<span data-ttu-id="cb0a6-116">描述</span><span class="sxs-lookup"><span data-stu-id="cb0a6-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="cb0a6-117">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb0a6-118">範例</span><span class="sxs-lookup"><span data-stu-id="cb0a6-118">Example</span></span>  
 <span data-ttu-id="cb0a6-119">下列 XML 顯示如何使用和專案， `<add>` `<remove>` 以自訂會話權杖處理常式取代預設會話權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="cb0a6-120">XML 取自 `ClaimsAwareWebFarm` 範例。</span><span class="sxs-lookup"><span data-stu-id="cb0a6-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
