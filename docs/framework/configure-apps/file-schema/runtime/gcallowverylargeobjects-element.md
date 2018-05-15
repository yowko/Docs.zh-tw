---
title: '&lt;gcAllowVeryLargeObjects&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 750b0dbc925ec484dd80e1796ba991435e354709
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="48e58-102">&lt;gcAllowVeryLargeObjects&gt;項目</span><span class="sxs-lookup"><span data-stu-id="48e58-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="48e58-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="48e58-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="48e58-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="48e58-104">\<configuration> Element</span></span>  
<span data-ttu-id="48e58-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="48e58-105">\<runtime> Element</span></span>  
<span data-ttu-id="48e58-106">\<gcAllowVeryLargeObjects > 項目</span><span class="sxs-lookup"><span data-stu-id="48e58-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e58-107">語法</span><span class="sxs-lookup"><span data-stu-id="48e58-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48e58-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="48e58-108">Attributes and Elements</span></span>  
 <span data-ttu-id="48e58-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="48e58-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48e58-110">屬性</span><span class="sxs-lookup"><span data-stu-id="48e58-110">Attributes</span></span>  
  
|<span data-ttu-id="48e58-111">屬性</span><span class="sxs-lookup"><span data-stu-id="48e58-111">Attribute</span></span>|<span data-ttu-id="48e58-112">描述</span><span class="sxs-lookup"><span data-stu-id="48e58-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="48e58-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="48e58-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="48e58-114">指定是否在 64 位元平台上啟用的總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="48e58-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="48e58-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="48e58-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="48e58-116">值</span><span class="sxs-lookup"><span data-stu-id="48e58-116">Value</span></span>|<span data-ttu-id="48e58-117">描述</span><span class="sxs-lookup"><span data-stu-id="48e58-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="48e58-118">不會啟用大於 2 GB 的總大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="48e58-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="48e58-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="48e58-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="48e58-120">在 64 位元平台時啟用大於 2 GB 的總大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="48e58-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48e58-121">子項目</span><span class="sxs-lookup"><span data-stu-id="48e58-121">Child Elements</span></span>  
 <span data-ttu-id="48e58-122">無。</span><span class="sxs-lookup"><span data-stu-id="48e58-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48e58-123">父項目</span><span class="sxs-lookup"><span data-stu-id="48e58-123">Parent Elements</span></span>  
  
|<span data-ttu-id="48e58-124">項目</span><span class="sxs-lookup"><span data-stu-id="48e58-124">Element</span></span>|<span data-ttu-id="48e58-125">描述</span><span class="sxs-lookup"><span data-stu-id="48e58-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48e58-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="48e58-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="48e58-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="48e58-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e58-128">備註</span><span class="sxs-lookup"><span data-stu-id="48e58-128">Remarks</span></span>  
 <span data-ttu-id="48e58-129">在應用程式組態檔中使用這個項目可讓陣列是大於 2 GB 的大小，但不會變更其他物件的大小或陣列大小的限制：</span><span class="sxs-lookup"><span data-stu-id="48e58-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="48e58-130">陣列中元素的數目上限是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="48e58-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="48e58-131">2,147,483,591 (0x7FFFFFC7) 的位元組陣列和陣列的單一位元組結構，而其他類型的 2,146,435,071 (0X7FEFFFFF) 中任何單一維度的最大索引。</span><span class="sxs-lookup"><span data-stu-id="48e58-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="48e58-132">字串和其他非陣列物件的大小上限不會變更。</span><span class="sxs-lookup"><span data-stu-id="48e58-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="48e58-133">之前啟用此功能，請確定您的應用程式不包含假設所有陣列都都小於 2 GB 大小的 unsafe 程式碼。</span><span class="sxs-lookup"><span data-stu-id="48e58-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="48e58-134">例如，使用陣列做為緩衝區的 unsafe 程式碼可能容易受到緩衝區滿溢如果撰寫假設陣列將不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="48e58-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e58-135">範例</span><span class="sxs-lookup"><span data-stu-id="48e58-135">Example</span></span>  
 <span data-ttu-id="48e58-136">下列範例會示範如何為應用程式啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="48e58-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48e58-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48e58-137">See Also</span></span>  
 [<span data-ttu-id="48e58-138">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="48e58-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="48e58-139">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="48e58-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
