---
title: '&lt;remove&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: 5
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: fb62bbe8b52032708dddd62dd895e61ba8c1c5e9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltremovegt"></a><span data-ttu-id="d7dcc-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="d7dcc-102">&lt;remove&gt;</span></span>
<span data-ttu-id="d7dcc-103">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="d7dcc-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d7dcc-104">\<system.identityModel></span></span>  
<span data-ttu-id="d7dcc-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d7dcc-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d7dcc-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d7dcc-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d7dcc-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="d7dcc-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7dcc-108">語法</span><span class="sxs-lookup"><span data-stu-id="d7dcc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7dcc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7dcc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d7dcc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7dcc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d7dcc-111">Attributes</span></span>  
  
|<span data-ttu-id="d7dcc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d7dcc-112">Attribute</span></span>|<span data-ttu-id="d7dcc-113">描述</span><span class="sxs-lookup"><span data-stu-id="d7dcc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7dcc-114">類型</span><span class="sxs-lookup"><span data-stu-id="d7dcc-114">type</span></span>|<span data-ttu-id="d7dcc-115">要移除的語彙基元處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="d7dcc-116">如需有關如何指定`type`屬性，請參閱[自訂型別參考](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="d7dcc-117">必要。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7dcc-118">子元素</span><span class="sxs-lookup"><span data-stu-id="d7dcc-118">Child Elements</span></span>  
 <span data-ttu-id="d7dcc-119">無</span><span class="sxs-lookup"><span data-stu-id="d7dcc-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7dcc-120">父項目</span><span class="sxs-lookup"><span data-stu-id="d7dcc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d7dcc-121">項目</span><span class="sxs-lookup"><span data-stu-id="d7dcc-121">Element</span></span>|<span data-ttu-id="d7dcc-122">描述</span><span class="sxs-lookup"><span data-stu-id="d7dcc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7dcc-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d7dcc-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="d7dcc-124">指定註冊的端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7dcc-125">範例</span><span class="sxs-lookup"><span data-stu-id="d7dcc-125">Example</span></span>  
 <span data-ttu-id="d7dcc-126">下列 XML 程式碼將示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設工作階段權杖處理常式項目。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d7dcc-127">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="d7dcc-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
