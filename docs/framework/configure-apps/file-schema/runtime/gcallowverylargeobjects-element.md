---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6af994284a56c573d70f3688ccec16459b8eed59
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273370"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="d9c74-102">\<Gcallowverylargeobjects> > 項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="d9c74-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="d9c74-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="d9c74-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-104">\<configuration> Element</span></span>  
<span data-ttu-id="d9c74-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-105">\<runtime> Element</span></span>  
<span data-ttu-id="d9c74-106">\<Gcallowverylargeobjects> > 項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c74-107">語法</span><span class="sxs-lookup"><span data-stu-id="d9c74-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9c74-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9c74-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d9c74-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9c74-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d9c74-110">Attributes</span></span>  
  
|<span data-ttu-id="d9c74-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d9c74-111">Attribute</span></span>|<span data-ttu-id="d9c74-112">描述</span><span class="sxs-lookup"><span data-stu-id="d9c74-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d9c74-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d9c74-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d9c74-114">指定是否在 64 位元平台上啟用的總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="d9c74-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d9c74-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d9c74-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d9c74-116">值</span><span class="sxs-lookup"><span data-stu-id="d9c74-116">Value</span></span>|<span data-ttu-id="d9c74-117">描述</span><span class="sxs-lookup"><span data-stu-id="d9c74-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d9c74-118">陣列大於 2 GB 的大小總計不會啟用。</span><span class="sxs-lookup"><span data-stu-id="d9c74-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="d9c74-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="d9c74-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d9c74-120">陣列大於 2 GB 的總大小是 64 位元平台上啟用。</span><span class="sxs-lookup"><span data-stu-id="d9c74-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9c74-121">子元素</span><span class="sxs-lookup"><span data-stu-id="d9c74-121">Child Elements</span></span>  
 <span data-ttu-id="d9c74-122">無。</span><span class="sxs-lookup"><span data-stu-id="d9c74-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9c74-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d9c74-124">項目</span><span class="sxs-lookup"><span data-stu-id="d9c74-124">Element</span></span>|<span data-ttu-id="d9c74-125">描述</span><span class="sxs-lookup"><span data-stu-id="d9c74-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d9c74-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d9c74-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d9c74-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="d9c74-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9c74-128">備註</span><span class="sxs-lookup"><span data-stu-id="d9c74-128">Remarks</span></span>  
 <span data-ttu-id="d9c74-129">使用您的應用程式組態檔中此項目會啟用大於 2 GB 大小的陣列，但不會變更的物件大小或陣列大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="d9c74-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="d9c74-130">陣列中的項目數目上限是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d9c74-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="d9c74-131">2,147,483,591 (0x7FFFFFC7) 的位元組陣列與單一位元組結構的陣列和其他類型的 2,146,435,071 (0X7FEFFFFF) 中任何單一維度的最大的索引。</span><span class="sxs-lookup"><span data-stu-id="d9c74-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="d9c74-132">字串和其他非陣列物件的大小上限不會變更。</span><span class="sxs-lookup"><span data-stu-id="d9c74-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d9c74-133">之前啟用這項功能，請確定您的應用程式不包含不安全的程式碼假設所有陣列都是小於 2 GB 的大小。</span><span class="sxs-lookup"><span data-stu-id="d9c74-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="d9c74-134">例如，陣列做為緩衝區的 unsafe 程式碼可能容易發生緩衝區溢位如果寫入假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="d9c74-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c74-135">範例</span><span class="sxs-lookup"><span data-stu-id="d9c74-135">Example</span></span>  
 <span data-ttu-id="d9c74-136">下列範例示範如何啟用此功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9c74-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9c74-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9c74-137">See also</span></span>
- [<span data-ttu-id="d9c74-138">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d9c74-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d9c74-139">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d9c74-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
