---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 410fef1a43f9202d56c4957b1162c53ee056ae3f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074910"
---
# <a name="ltremovegt"></a><span data-ttu-id="fc469-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="fc469-102">&lt;remove&gt;</span></span>
<span data-ttu-id="fc469-103">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="fc469-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="fc469-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fc469-104">\<system.identityModel></span></span>  
<span data-ttu-id="fc469-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fc469-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fc469-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fc469-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fc469-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="fc469-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc469-108">語法</span><span class="sxs-lookup"><span data-stu-id="fc469-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc469-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fc469-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc469-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fc469-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc469-111">屬性</span><span class="sxs-lookup"><span data-stu-id="fc469-111">Attributes</span></span>  
  
|<span data-ttu-id="fc469-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fc469-112">Attribute</span></span>|<span data-ttu-id="fc469-113">描述</span><span class="sxs-lookup"><span data-stu-id="fc469-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc469-114">類型</span><span class="sxs-lookup"><span data-stu-id="fc469-114">type</span></span>|<span data-ttu-id="fc469-115">要移除的權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="fc469-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="fc469-116">如需有關如何指定`type`屬性，請參閱[自訂型別參考](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。</span><span class="sxs-lookup"><span data-stu-id="fc469-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="fc469-117">必要。</span><span class="sxs-lookup"><span data-stu-id="fc469-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc469-118">子元素</span><span class="sxs-lookup"><span data-stu-id="fc469-118">Child Elements</span></span>  
 <span data-ttu-id="fc469-119">無</span><span class="sxs-lookup"><span data-stu-id="fc469-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc469-120">父項目</span><span class="sxs-lookup"><span data-stu-id="fc469-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fc469-121">項目</span><span class="sxs-lookup"><span data-stu-id="fc469-121">Element</span></span>|<span data-ttu-id="fc469-122">描述</span><span class="sxs-lookup"><span data-stu-id="fc469-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc469-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fc469-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="fc469-124">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="fc469-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc469-125">範例</span><span class="sxs-lookup"><span data-stu-id="fc469-125">Example</span></span>  
 <span data-ttu-id="fc469-126">下列 XML 示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設的工作階段權杖處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="fc469-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="fc469-127">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="fc469-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
