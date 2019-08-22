---
title: < Crst_DisableSpinWait > 元素
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663832"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="d7b36-102">\<Crst_DisableSpinWait > 元素</span><span class="sxs-lookup"><span data-stu-id="d7b36-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="d7b36-103">指定是否要在爭用時停用微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="d7b36-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="d7b36-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d7b36-104">\<configuration></span></span>  
<span data-ttu-id="d7b36-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="d7b36-105">\<runtime></span></span>  
<span data-ttu-id="d7b36-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="d7b36-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b36-107">語法</span><span class="sxs-lookup"><span data-stu-id="d7b36-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b36-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d7b36-108">Attributes and Elements</span></span>

<span data-ttu-id="d7b36-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d7b36-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b36-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d7b36-110">Attributes</span></span>  
  
|<span data-ttu-id="d7b36-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d7b36-111">Attribute</span></span>|<span data-ttu-id="d7b36-112">描述</span><span class="sxs-lookup"><span data-stu-id="d7b36-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7b36-113">**enabled**</span><span class="sxs-lookup"><span data-stu-id="d7b36-113">**enabled**</span></span>|<span data-ttu-id="d7b36-114">指定在停用時, 是否要微調等候重要區段。</span><span class="sxs-lookup"><span data-stu-id="d7b36-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d7b36-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d7b36-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d7b36-116">值</span><span class="sxs-lookup"><span data-stu-id="d7b36-116">Value</span></span>|<span data-ttu-id="d7b36-117">描述</span><span class="sxs-lookup"><span data-stu-id="d7b36-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d7b36-118">1</span><span class="sxs-lookup"><span data-stu-id="d7b36-118">1</span></span>|<span data-ttu-id="d7b36-119">當無法取得重要區段時, 停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="d7b36-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="d7b36-120">0</span><span class="sxs-lookup"><span data-stu-id="d7b36-120">0</span></span>|<span data-ttu-id="d7b36-121">當無法取得重要區段時, 請勿停用微調等候。</span><span class="sxs-lookup"><span data-stu-id="d7b36-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="d7b36-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="d7b36-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7b36-123">子元素</span><span class="sxs-lookup"><span data-stu-id="d7b36-123">Child Elements</span></span>  
 <span data-ttu-id="d7b36-124">無。</span><span class="sxs-lookup"><span data-stu-id="d7b36-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b36-125">父項目</span><span class="sxs-lookup"><span data-stu-id="d7b36-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b36-126">項目</span><span class="sxs-lookup"><span data-stu-id="d7b36-126">Element</span></span>|<span data-ttu-id="d7b36-127">描述</span><span class="sxs-lookup"><span data-stu-id="d7b36-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d7b36-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d7b36-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d7b36-129">包含各種執行時間設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d7b36-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7b36-130">範例</span><span class="sxs-lookup"><span data-stu-id="d7b36-130">Example</span></span>  

<span data-ttu-id="d7b36-131">下列範例會在爭用時停用關鍵區段中的微調等候。</span><span class="sxs-lookup"><span data-stu-id="d7b36-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7b36-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7b36-132">See also</span></span>

- [<span data-ttu-id="d7b36-133">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d7b36-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d7b36-134">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d7b36-134">Configuration File Schema</span></span>](../index.md)
