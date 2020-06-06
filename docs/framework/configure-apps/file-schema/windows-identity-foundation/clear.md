---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252037"
---
# \<clear>
<span data-ttu-id="46b88-101">清除目前權杖處理常式集合中的所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="46b88-101">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="46b88-102">語法</span><span class="sxs-lookup"><span data-stu-id="46b88-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46b88-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="46b88-103">Attributes and Elements</span></span>  
 <span data-ttu-id="46b88-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46b88-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46b88-105">屬性</span><span class="sxs-lookup"><span data-stu-id="46b88-105">Attributes</span></span>  
 <span data-ttu-id="46b88-106">無</span><span class="sxs-lookup"><span data-stu-id="46b88-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="46b88-107">子元素</span><span class="sxs-lookup"><span data-stu-id="46b88-107">Child Elements</span></span>  
 <span data-ttu-id="46b88-108">無</span><span class="sxs-lookup"><span data-stu-id="46b88-108">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46b88-109">父項目</span><span class="sxs-lookup"><span data-stu-id="46b88-109">Parent Elements</span></span>  
  
|<span data-ttu-id="46b88-110">元素</span><span class="sxs-lookup"><span data-stu-id="46b88-110">Element</span></span>|<span data-ttu-id="46b88-111">描述</span><span class="sxs-lookup"><span data-stu-id="46b88-111">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="46b88-112">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="46b88-112">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
