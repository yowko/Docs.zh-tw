---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152537"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="c5caa-101">\<會話權杖要求></span><span class="sxs-lookup"><span data-stu-id="c5caa-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="c5caa-102">提供類或派生<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類的配置。</span><span class="sxs-lookup"><span data-stu-id="c5caa-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="c5caa-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5caa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5caa-104">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c5caa-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c5caa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c5caa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c5caa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c5caa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c5caa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="c5caa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c5caa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<會話權杖要求>**</span><span class="sxs-lookup"><span data-stu-id="c5caa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5caa-109">語法</span><span class="sxs-lookup"><span data-stu-id="c5caa-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5caa-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c5caa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5caa-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c5caa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5caa-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c5caa-112">Attributes</span></span>  
  
|<span data-ttu-id="c5caa-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c5caa-113">Attribute</span></span>|<span data-ttu-id="c5caa-114">描述</span><span class="sxs-lookup"><span data-stu-id="c5caa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5caa-115">lifetime</span><span class="sxs-lookup"><span data-stu-id="c5caa-115">lifetime</span></span>|<span data-ttu-id="c5caa-116">指定會話權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="c5caa-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5caa-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c5caa-117">Child Elements</span></span>  
 <span data-ttu-id="c5caa-118">None</span><span class="sxs-lookup"><span data-stu-id="c5caa-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5caa-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c5caa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c5caa-120">元素</span><span class="sxs-lookup"><span data-stu-id="c5caa-120">Element</span></span>|<span data-ttu-id="c5caa-121">描述</span><span class="sxs-lookup"><span data-stu-id="c5caa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5caa-122">\<添加></span><span class="sxs-lookup"><span data-stu-id="c5caa-122">\<add></span></span>](add.md)|<span data-ttu-id="c5caa-123">將指定的安全權杖處理常式添加到權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="c5caa-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5caa-124">範例</span><span class="sxs-lookup"><span data-stu-id="c5caa-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
