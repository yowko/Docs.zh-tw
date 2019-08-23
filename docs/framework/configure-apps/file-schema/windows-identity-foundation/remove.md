---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 11aeed0277fc13cbd9a65232311bd575a4a81ff7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942575"
---
# <a name="remove"></a><span data-ttu-id="eb460-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="eb460-101">\<remove></span></span>
<span data-ttu-id="eb460-102">從權杖處理常式集合中移除指定的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="eb460-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="eb460-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="eb460-103">\<system.identityModel></span></span>  
<span data-ttu-id="eb460-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="eb460-104">\<identityConfiguration></span></span>  
<span data-ttu-id="eb460-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="eb460-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="eb460-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="eb460-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb460-107">語法</span><span class="sxs-lookup"><span data-stu-id="eb460-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb460-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eb460-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eb460-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eb460-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb460-110">屬性</span><span class="sxs-lookup"><span data-stu-id="eb460-110">Attributes</span></span>  
  
|<span data-ttu-id="eb460-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eb460-111">Attribute</span></span>|<span data-ttu-id="eb460-112">描述</span><span class="sxs-lookup"><span data-stu-id="eb460-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb460-113">型別</span><span class="sxs-lookup"><span data-stu-id="eb460-113">type</span></span>|<span data-ttu-id="eb460-114">要移除之權杖處理常式的 CLR 型別名稱。</span><span class="sxs-lookup"><span data-stu-id="eb460-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="eb460-115">如需如何指定屬性的`type`詳細資訊, 請參閱[自訂類型參考](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references)。</span><span class="sxs-lookup"><span data-stu-id="eb460-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="eb460-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="eb460-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb460-117">子元素</span><span class="sxs-lookup"><span data-stu-id="eb460-117">Child Elements</span></span>  
 <span data-ttu-id="eb460-118">None</span><span class="sxs-lookup"><span data-stu-id="eb460-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb460-119">父項目</span><span class="sxs-lookup"><span data-stu-id="eb460-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eb460-120">項目</span><span class="sxs-lookup"><span data-stu-id="eb460-120">Element</span></span>|<span data-ttu-id="eb460-121">說明</span><span class="sxs-lookup"><span data-stu-id="eb460-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb460-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="eb460-122">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="eb460-123">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="eb460-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eb460-124">範例</span><span class="sxs-lookup"><span data-stu-id="eb460-124">Example</span></span>  
 <span data-ttu-id="eb460-125">下列 XML 顯示如何使用`<add>`和`<remove>`專案, 以自訂會話權杖處理常式取代預設會話權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="eb460-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="eb460-126">XML 取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="eb460-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
