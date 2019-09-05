---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251821"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="9ce3b-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="9ce3b-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="9ce3b-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="9ce3b-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="9ce3b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ce3b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9ce3b-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="9ce3b-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="9ce3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9ce3b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="9ce3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="9ce3b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="9ce3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="9ce3b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="9ce3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Sessiontokenrequirement lifetime >**</span><span class="sxs-lookup"><span data-stu-id="9ce3b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce3b-109">語法</span><span class="sxs-lookup"><span data-stu-id="9ce3b-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ce3b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9ce3b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ce3b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9ce3b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ce3b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9ce3b-112">Attributes</span></span>  
  
|<span data-ttu-id="9ce3b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9ce3b-113">Attribute</span></span>|<span data-ttu-id="9ce3b-114">說明</span><span class="sxs-lookup"><span data-stu-id="9ce3b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ce3b-115">存留期</span><span class="sxs-lookup"><span data-stu-id="9ce3b-115">lifetime</span></span>|<span data-ttu-id="9ce3b-116">指定會話權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="9ce3b-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ce3b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9ce3b-117">Child Elements</span></span>  
 <span data-ttu-id="9ce3b-118">無</span><span class="sxs-lookup"><span data-stu-id="9ce3b-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ce3b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9ce3b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9ce3b-120">項目</span><span class="sxs-lookup"><span data-stu-id="9ce3b-120">Element</span></span>|<span data-ttu-id="9ce3b-121">描述</span><span class="sxs-lookup"><span data-stu-id="9ce3b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ce3b-122">\<add></span><span class="sxs-lookup"><span data-stu-id="9ce3b-122">\<add></span></span>](add.md)|<span data-ttu-id="9ce3b-123">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="9ce3b-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9ce3b-124">範例</span><span class="sxs-lookup"><span data-stu-id="9ce3b-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
