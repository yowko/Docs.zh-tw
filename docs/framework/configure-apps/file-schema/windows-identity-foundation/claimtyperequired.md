---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: a86265ba3963ebc8bea880befbcf80345529116d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203848"
---
# \<claimTypeRequired>

<span data-ttu-id="758ea-101">指定傳入安全性權杖所需的宣告集。</span><span class="sxs-lookup"><span data-stu-id="758ea-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="758ea-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="758ea-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="758ea-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="758ea-103">Attributes and Elements</span></span>  

 <span data-ttu-id="758ea-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="758ea-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="758ea-105">屬性</span><span class="sxs-lookup"><span data-stu-id="758ea-105">Attributes</span></span>  

 <span data-ttu-id="758ea-106">無</span><span class="sxs-lookup"><span data-stu-id="758ea-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="758ea-107">子元素</span><span class="sxs-lookup"><span data-stu-id="758ea-107">Child Elements</span></span>  
  
|<span data-ttu-id="758ea-108">項目</span><span class="sxs-lookup"><span data-stu-id="758ea-108">Element</span></span>|<span data-ttu-id="758ea-109">描述</span><span class="sxs-lookup"><span data-stu-id="758ea-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="758ea-110">針對傳入的安全性權杖，指定單一選用或必要的宣告。</span><span class="sxs-lookup"><span data-stu-id="758ea-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="758ea-111">父項目</span><span class="sxs-lookup"><span data-stu-id="758ea-111">Parent Elements</span></span>  
  
|<span data-ttu-id="758ea-112">項目</span><span class="sxs-lookup"><span data-stu-id="758ea-112">Element</span></span>|<span data-ttu-id="758ea-113">描述</span><span class="sxs-lookup"><span data-stu-id="758ea-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="758ea-114">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="758ea-114">Specifies service-level identity settings.</span></span>|
