---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152537"
---
# \<sessionTokenRequirement>
<span data-ttu-id="4883c-101">提供 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> 類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="4883c-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="4883c-102">語法</span><span class="sxs-lookup"><span data-stu-id="4883c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4883c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4883c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4883c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4883c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4883c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4883c-105">Attributes</span></span>  
  
|<span data-ttu-id="4883c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4883c-106">Attribute</span></span>|<span data-ttu-id="4883c-107">描述</span><span class="sxs-lookup"><span data-stu-id="4883c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4883c-108">lifetime</span><span class="sxs-lookup"><span data-stu-id="4883c-108">lifetime</span></span>|<span data-ttu-id="4883c-109">指定會話權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="4883c-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4883c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4883c-110">Child Elements</span></span>  
 <span data-ttu-id="4883c-111">無</span><span class="sxs-lookup"><span data-stu-id="4883c-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4883c-112">父項目</span><span class="sxs-lookup"><span data-stu-id="4883c-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4883c-113">元素</span><span class="sxs-lookup"><span data-stu-id="4883c-113">Element</span></span>|<span data-ttu-id="4883c-114">描述</span><span class="sxs-lookup"><span data-stu-id="4883c-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="4883c-115">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="4883c-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4883c-116">範例</span><span class="sxs-lookup"><span data-stu-id="4883c-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
