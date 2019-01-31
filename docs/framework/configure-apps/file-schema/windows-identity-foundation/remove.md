---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: a54957458311e2d5941d1aa1c2486a2f66994d9b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288128"
---
# <a name="remove"></a><span data-ttu-id="6a7d8-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="6a7d8-101">\<remove></span></span>
<span data-ttu-id="6a7d8-102">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="6a7d8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6a7d8-103">\<system.identityModel></span></span>  
<span data-ttu-id="6a7d8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="6a7d8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="6a7d8-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6a7d8-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="6a7d8-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="6a7d8-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7d8-107">語法</span><span class="sxs-lookup"><span data-stu-id="6a7d8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a7d8-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6a7d8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6a7d8-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a7d8-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6a7d8-110">Attributes</span></span>  
  
|<span data-ttu-id="6a7d8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6a7d8-111">Attribute</span></span>|<span data-ttu-id="6a7d8-112">描述</span><span class="sxs-lookup"><span data-stu-id="6a7d8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a7d8-113">類型</span><span class="sxs-lookup"><span data-stu-id="6a7d8-113">type</span></span>|<span data-ttu-id="6a7d8-114">要移除的權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="6a7d8-115">如需有關如何指定`type`屬性，請參閱[自訂型別參考](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="6a7d8-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a7d8-117">子元素</span><span class="sxs-lookup"><span data-stu-id="6a7d8-117">Child Elements</span></span>  
 <span data-ttu-id="6a7d8-118">無</span><span class="sxs-lookup"><span data-stu-id="6a7d8-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a7d8-119">父項目</span><span class="sxs-lookup"><span data-stu-id="6a7d8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6a7d8-120">項目</span><span class="sxs-lookup"><span data-stu-id="6a7d8-120">Element</span></span>|<span data-ttu-id="6a7d8-121">描述</span><span class="sxs-lookup"><span data-stu-id="6a7d8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a7d8-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="6a7d8-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="6a7d8-123">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a7d8-124">範例</span><span class="sxs-lookup"><span data-stu-id="6a7d8-124">Example</span></span>  
 <span data-ttu-id="6a7d8-125">下列 XML 示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設的工作階段權杖處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="6a7d8-126">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="6a7d8-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
