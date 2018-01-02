---
title: "&lt;gcAllowVeryLargeObjects&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5db777f147e2eca7644d5b5f1a4bc18c8401ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="7a259-102">&lt;gcAllowVeryLargeObjects&gt;項目</span><span class="sxs-lookup"><span data-stu-id="7a259-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="7a259-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="7a259-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="7a259-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="7a259-104">\<configuration> Element</span></span>  
<span data-ttu-id="7a259-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="7a259-105">\<runtime> Element</span></span>  
<span data-ttu-id="7a259-106">\<gcAllowVeryLargeObjects > 項目</span><span class="sxs-lookup"><span data-stu-id="7a259-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a259-107">語法</span><span class="sxs-lookup"><span data-stu-id="7a259-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a259-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7a259-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a259-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7a259-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a259-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7a259-110">Attributes</span></span>  
  
|<span data-ttu-id="7a259-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7a259-111">Attribute</span></span>|<span data-ttu-id="7a259-112">描述</span><span class="sxs-lookup"><span data-stu-id="7a259-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7a259-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7a259-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a259-114">指定是否在 64 位元平台上啟用的總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="7a259-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7a259-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="7a259-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7a259-116">值</span><span class="sxs-lookup"><span data-stu-id="7a259-116">Value</span></span>|<span data-ttu-id="7a259-117">描述</span><span class="sxs-lookup"><span data-stu-id="7a259-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7a259-118">不會啟用大於 2 GB 的總大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="7a259-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="7a259-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="7a259-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="7a259-120">在 64 位元平台時啟用大於 2 GB 的總大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="7a259-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a259-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7a259-121">Child Elements</span></span>  
 <span data-ttu-id="7a259-122">無。</span><span class="sxs-lookup"><span data-stu-id="7a259-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a259-123">父項目</span><span class="sxs-lookup"><span data-stu-id="7a259-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7a259-124">項目</span><span class="sxs-lookup"><span data-stu-id="7a259-124">Element</span></span>|<span data-ttu-id="7a259-125">描述</span><span class="sxs-lookup"><span data-stu-id="7a259-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7a259-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7a259-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7a259-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="7a259-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a259-128">備註</span><span class="sxs-lookup"><span data-stu-id="7a259-128">Remarks</span></span>  
 <span data-ttu-id="7a259-129">在應用程式組態檔中使用這個項目可讓陣列是大於 2 GB 的大小，但不會變更其他物件的大小或陣列大小的限制：</span><span class="sxs-lookup"><span data-stu-id="7a259-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="7a259-130">陣列中元素的數目上限是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7a259-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="7a259-131">2,147,483,591 (0x7FFFFFC7) 的位元組陣列和陣列的單一位元組結構，而其他類型的 2,146,435,071 (0X7FEFFFFF) 中任何單一維度的最大索引。</span><span class="sxs-lookup"><span data-stu-id="7a259-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="7a259-132">字串和其他非陣列物件的大小上限不會變更。</span><span class="sxs-lookup"><span data-stu-id="7a259-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="7a259-133">之前啟用此功能，請確定您的應用程式不包含假設所有陣列都都小於 2 GB 大小的 unsafe 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7a259-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="7a259-134">例如，使用陣列做為緩衝區的 unsafe 程式碼可能容易受到緩衝區滿溢如果撰寫假設陣列將不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="7a259-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a259-135">範例</span><span class="sxs-lookup"><span data-stu-id="7a259-135">Example</span></span>  
 <span data-ttu-id="7a259-136">下列範例會示範如何為應用程式啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="7a259-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a259-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a259-137">See Also</span></span>  
 [<span data-ttu-id="7a259-138">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7a259-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="7a259-139">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7a259-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
