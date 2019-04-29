---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793883"
---
# <a name="remove"></a><span data-ttu-id="dbee1-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="dbee1-101">\<remove></span></span>
<span data-ttu-id="dbee1-102">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="dbee1-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="dbee1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="dbee1-103">\<system.identityModel></span></span>  
<span data-ttu-id="dbee1-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="dbee1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="dbee1-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="dbee1-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="dbee1-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="dbee1-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbee1-107">語法</span><span class="sxs-lookup"><span data-stu-id="dbee1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbee1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dbee1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dbee1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dbee1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbee1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dbee1-110">Attributes</span></span>  
  
|<span data-ttu-id="dbee1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dbee1-111">Attribute</span></span>|<span data-ttu-id="dbee1-112">描述</span><span class="sxs-lookup"><span data-stu-id="dbee1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbee1-113">類型</span><span class="sxs-lookup"><span data-stu-id="dbee1-113">type</span></span>|<span data-ttu-id="dbee1-114">要移除的權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="dbee1-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="dbee1-115">如需有關如何指定`type`屬性，請參閱[自訂型別參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="dbee1-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="dbee1-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="dbee1-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbee1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="dbee1-117">Child Elements</span></span>  
 <span data-ttu-id="dbee1-118">None</span><span class="sxs-lookup"><span data-stu-id="dbee1-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbee1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="dbee1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dbee1-120">項目</span><span class="sxs-lookup"><span data-stu-id="dbee1-120">Element</span></span>|<span data-ttu-id="dbee1-121">描述</span><span class="sxs-lookup"><span data-stu-id="dbee1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbee1-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="dbee1-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="dbee1-123">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="dbee1-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dbee1-124">範例</span><span class="sxs-lookup"><span data-stu-id="dbee1-124">Example</span></span>  
 <span data-ttu-id="dbee1-125">下列 XML 示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設的工作階段權杖處理常式的項目。</span><span class="sxs-lookup"><span data-stu-id="dbee1-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="dbee1-126">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="dbee1-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
