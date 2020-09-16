---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 7581f581c4b97a07eb4bdeb49eb5ae5ce72c2aa7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535712"
---
# \<remove>
<span data-ttu-id="7d3bb-101">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-101">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="7d3bb-102">語法</span><span class="sxs-lookup"><span data-stu-id="7d3bb-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d3bb-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7d3bb-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7d3bb-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d3bb-105">屬性</span><span class="sxs-lookup"><span data-stu-id="7d3bb-105">Attributes</span></span>  
  
|<span data-ttu-id="7d3bb-106">屬性</span><span class="sxs-lookup"><span data-stu-id="7d3bb-106">Attribute</span></span>|<span data-ttu-id="7d3bb-107">描述</span><span class="sxs-lookup"><span data-stu-id="7d3bb-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d3bb-108">type</span><span class="sxs-lookup"><span data-stu-id="7d3bb-108">type</span></span>|<span data-ttu-id="7d3bb-109">要移除之 token 處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-109">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="7d3bb-110">如需如何指定屬性的詳細資訊 `type` ，請參閱 [自訂型別參考](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-110">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="7d3bb-111">必要。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-111">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d3bb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7d3bb-112">Child Elements</span></span>  
 <span data-ttu-id="7d3bb-113">None</span><span class="sxs-lookup"><span data-stu-id="7d3bb-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d3bb-114">父項目</span><span class="sxs-lookup"><span data-stu-id="7d3bb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7d3bb-115">項目</span><span class="sxs-lookup"><span data-stu-id="7d3bb-115">Element</span></span>|<span data-ttu-id="7d3bb-116">描述</span><span class="sxs-lookup"><span data-stu-id="7d3bb-116">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="7d3bb-117">指定向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-117">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d3bb-118">範例</span><span class="sxs-lookup"><span data-stu-id="7d3bb-118">Example</span></span>  
 <span data-ttu-id="7d3bb-119">下列 XML 會示範如何使用和專案 `<add>` ， `<remove>` 以自訂會話權杖處理常式來取代預設的會話 token 處理常式。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-119">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="7d3bb-120">XML 取自 `ClaimsAwareWebFarm` 範例。</span><span class="sxs-lookup"><span data-stu-id="7d3bb-120">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
