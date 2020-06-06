---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251740"
---
# \<userNameSecurityTokenHandlerRequirement>
<span data-ttu-id="78f12-101">提供 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="78f12-101">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="78f12-102">語法</span><span class="sxs-lookup"><span data-stu-id="78f12-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78f12-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78f12-103">Attributes and Elements</span></span>  
 <span data-ttu-id="78f12-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="78f12-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78f12-105">屬性</span><span class="sxs-lookup"><span data-stu-id="78f12-105">Attributes</span></span>  
  
|<span data-ttu-id="78f12-106">屬性</span><span class="sxs-lookup"><span data-stu-id="78f12-106">Attribute</span></span>|<span data-ttu-id="78f12-107">描述</span><span class="sxs-lookup"><span data-stu-id="78f12-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78f12-108">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="78f12-108">membershipProviderName</span></span>|<span data-ttu-id="78f12-109">指定 <xref:System.Web.Security.MembershipProvider> 安全性權杖處理常式應該使用的。</span><span class="sxs-lookup"><span data-stu-id="78f12-109">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78f12-110">子元素</span><span class="sxs-lookup"><span data-stu-id="78f12-110">Child Elements</span></span>  
 <span data-ttu-id="78f12-111">無</span><span class="sxs-lookup"><span data-stu-id="78f12-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78f12-112">父項目</span><span class="sxs-lookup"><span data-stu-id="78f12-112">Parent Elements</span></span>  
  
|<span data-ttu-id="78f12-113">元素</span><span class="sxs-lookup"><span data-stu-id="78f12-113">Element</span></span>|<span data-ttu-id="78f12-114">描述</span><span class="sxs-lookup"><span data-stu-id="78f12-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="78f12-115">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="78f12-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f12-116">備註</span><span class="sxs-lookup"><span data-stu-id="78f12-116">Remarks</span></span>  
 <span data-ttu-id="78f12-117">`<userNameSecurityTokenHandlerRequirement>`元素 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> 會在物件從設定初始化時設定屬性 <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="78f12-117">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78f12-118">範例</span><span class="sxs-lookup"><span data-stu-id="78f12-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
