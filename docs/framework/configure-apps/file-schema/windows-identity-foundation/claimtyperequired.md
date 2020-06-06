---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252056"
---
# \<claimTypeRequired>
<span data-ttu-id="93e7c-101">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="93e7c-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="93e7c-102">語法</span><span class="sxs-lookup"><span data-stu-id="93e7c-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93e7c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93e7c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="93e7c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="93e7c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93e7c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="93e7c-105">Attributes</span></span>  
 <span data-ttu-id="93e7c-106">無</span><span class="sxs-lookup"><span data-stu-id="93e7c-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93e7c-107">子元素</span><span class="sxs-lookup"><span data-stu-id="93e7c-107">Child Elements</span></span>  
  
|<span data-ttu-id="93e7c-108">元素</span><span class="sxs-lookup"><span data-stu-id="93e7c-108">Element</span></span>|<span data-ttu-id="93e7c-109">描述</span><span class="sxs-lookup"><span data-stu-id="93e7c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="93e7c-110">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="93e7c-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93e7c-111">父項目</span><span class="sxs-lookup"><span data-stu-id="93e7c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="93e7c-112">元素</span><span class="sxs-lookup"><span data-stu-id="93e7c-112">Element</span></span>|<span data-ttu-id="93e7c-113">描述</span><span class="sxs-lookup"><span data-stu-id="93e7c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="93e7c-114">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="93e7c-114">Specifies service-level identity settings.</span></span>|
