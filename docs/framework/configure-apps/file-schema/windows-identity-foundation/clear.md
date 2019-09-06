---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252037"
---
# <a name="clear"></a><span data-ttu-id="47a44-101">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="47a44-101">\<clear></span></span>
<span data-ttu-id="47a44-102">清除目前權杖處理常式集合中的所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="47a44-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="47a44-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="47a44-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47a44-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="47a44-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="47a44-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="47a44-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="47a44-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="47a44-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="47a44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<清除 >**</span><span class="sxs-lookup"><span data-stu-id="47a44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a44-108">語法</span><span class="sxs-lookup"><span data-stu-id="47a44-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47a44-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="47a44-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47a44-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="47a44-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47a44-111">屬性</span><span class="sxs-lookup"><span data-stu-id="47a44-111">Attributes</span></span>  
 <span data-ttu-id="47a44-112">無</span><span class="sxs-lookup"><span data-stu-id="47a44-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="47a44-113">子元素</span><span class="sxs-lookup"><span data-stu-id="47a44-113">Child Elements</span></span>  
 <span data-ttu-id="47a44-114">無</span><span class="sxs-lookup"><span data-stu-id="47a44-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47a44-115">父項目</span><span class="sxs-lookup"><span data-stu-id="47a44-115">Parent Elements</span></span>  
  
|<span data-ttu-id="47a44-116">項目</span><span class="sxs-lookup"><span data-stu-id="47a44-116">Element</span></span>|<span data-ttu-id="47a44-117">說明</span><span class="sxs-lookup"><span data-stu-id="47a44-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47a44-118">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="47a44-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="47a44-119">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="47a44-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
