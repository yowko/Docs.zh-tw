---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: 0f043442fb8edd9bf95a839a26cc42e8122d9100
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167063"
---
# \<clear>

<span data-ttu-id="afadf-101">從目前的權杖處理常式集合中清除所有安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="afadf-101">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="afadf-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="afadf-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afadf-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="afadf-103">Attributes and Elements</span></span>  

 <span data-ttu-id="afadf-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="afadf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afadf-105">屬性</span><span class="sxs-lookup"><span data-stu-id="afadf-105">Attributes</span></span>  

 <span data-ttu-id="afadf-106">無</span><span class="sxs-lookup"><span data-stu-id="afadf-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afadf-107">子元素</span><span class="sxs-lookup"><span data-stu-id="afadf-107">Child Elements</span></span>  

 <span data-ttu-id="afadf-108">無</span><span class="sxs-lookup"><span data-stu-id="afadf-108">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afadf-109">父項目</span><span class="sxs-lookup"><span data-stu-id="afadf-109">Parent Elements</span></span>  
  
|<span data-ttu-id="afadf-110">項目</span><span class="sxs-lookup"><span data-stu-id="afadf-110">Element</span></span>|<span data-ttu-id="afadf-111">描述</span><span class="sxs-lookup"><span data-stu-id="afadf-111">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="afadf-112">指定向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="afadf-112">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
