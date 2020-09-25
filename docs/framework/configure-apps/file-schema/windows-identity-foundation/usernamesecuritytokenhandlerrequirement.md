---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: a49b41c04c8f184188b62e04c3b232bd33752fca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185518"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="74e49-101">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="74e49-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="74e49-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="74e49-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74e49-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74e49-103">Attributes and Elements</span></span>  

 <span data-ttu-id="74e49-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="74e49-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74e49-105">屬性</span><span class="sxs-lookup"><span data-stu-id="74e49-105">Attributes</span></span>  
  
|<span data-ttu-id="74e49-106">屬性</span><span class="sxs-lookup"><span data-stu-id="74e49-106">Attribute</span></span>|<span data-ttu-id="74e49-107">描述</span><span class="sxs-lookup"><span data-stu-id="74e49-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74e49-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="74e49-108">membershipProviderName</span></span>|<span data-ttu-id="74e49-109">指定 <xref:System.Web.Security.MembershipProvider> 安全性權杖處理常式應該使用的。</span><span class="sxs-lookup"><span data-stu-id="74e49-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74e49-110">子元素</span><span class="sxs-lookup"><span data-stu-id="74e49-110">Child Elements</span></span>  

 <span data-ttu-id="74e49-111">無</span><span class="sxs-lookup"><span data-stu-id="74e49-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74e49-112">父項目</span><span class="sxs-lookup"><span data-stu-id="74e49-112">Parent Elements</span></span>  
  
|<span data-ttu-id="74e49-113">項目</span><span class="sxs-lookup"><span data-stu-id="74e49-113">Element</span></span>|<span data-ttu-id="74e49-114">描述</span><span class="sxs-lookup"><span data-stu-id="74e49-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="74e49-115">將指定的安全性權杖處理常式新增至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="74e49-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74e49-116">備註</span><span class="sxs-lookup"><span data-stu-id="74e49-116">Remarks</span></span>  

 <span data-ttu-id="74e49-117">`<userNameSecurityTokenHandlerRequirement>` <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> 當物件從設定初始化時，元素會設定屬性 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="74e49-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74e49-118">範例</span><span class="sxs-lookup"><span data-stu-id="74e49-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
