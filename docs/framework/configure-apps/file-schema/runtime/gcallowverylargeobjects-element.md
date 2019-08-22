---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6db26d250de191559fdae0479aca9f41c147502
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663702"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="8a90e-102">\<Gcallowverylargeobjects> > 元素</span><span class="sxs-lookup"><span data-stu-id="8a90e-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="8a90e-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="8a90e-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="8a90e-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="8a90e-104">\<configuration> Element</span></span>  
<span data-ttu-id="8a90e-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="8a90e-105">\<runtime> Element</span></span>  
<span data-ttu-id="8a90e-106">\<Gcallowverylargeobjects> > 元素</span><span class="sxs-lookup"><span data-stu-id="8a90e-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a90e-107">語法</span><span class="sxs-lookup"><span data-stu-id="8a90e-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a90e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8a90e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8a90e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8a90e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a90e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8a90e-110">Attributes</span></span>  
  
|<span data-ttu-id="8a90e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8a90e-111">Attribute</span></span>|<span data-ttu-id="8a90e-112">描述</span><span class="sxs-lookup"><span data-stu-id="8a90e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8a90e-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8a90e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8a90e-114">指定在64位平臺上, 是否已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="8a90e-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8a90e-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="8a90e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8a90e-116">值</span><span class="sxs-lookup"><span data-stu-id="8a90e-116">Value</span></span>|<span data-ttu-id="8a90e-117">說明</span><span class="sxs-lookup"><span data-stu-id="8a90e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8a90e-118">未啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="8a90e-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="8a90e-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="8a90e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8a90e-120">64位平臺上已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="8a90e-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a90e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="8a90e-121">Child Elements</span></span>  
 <span data-ttu-id="8a90e-122">無。</span><span class="sxs-lookup"><span data-stu-id="8a90e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a90e-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8a90e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8a90e-124">項目</span><span class="sxs-lookup"><span data-stu-id="8a90e-124">Element</span></span>|<span data-ttu-id="8a90e-125">描述</span><span class="sxs-lookup"><span data-stu-id="8a90e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8a90e-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8a90e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8a90e-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="8a90e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a90e-128">備註</span><span class="sxs-lookup"><span data-stu-id="8a90e-128">Remarks</span></span>  
 <span data-ttu-id="8a90e-129">在您的應用程式佈建檔中使用此元素, 可讓大小大於 2 GB 的陣列, 但不會變更物件大小或陣列大小的其他限制:</span><span class="sxs-lookup"><span data-stu-id="8a90e-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="8a90e-130">陣列中的元素數目上限為<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8a90e-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="8a90e-131">任何單一維度中的最大索引為 2147483591 (0x7FFFFFC7), 適用于位元組陣列和單一位元組結構的陣列, 以及適用于其他類型的 2146435071 (0X7FEFFFFF)。</span><span class="sxs-lookup"><span data-stu-id="8a90e-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="8a90e-132">字串和其他非陣列物件的大小上限不變。</span><span class="sxs-lookup"><span data-stu-id="8a90e-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a90e-133">啟用這項功能之前, 請確定您的應用程式不包含不安全的程式碼, 其假設所有的陣列大小都小於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="8a90e-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="8a90e-134">例如, 如果不安全的程式碼是以陣列做為緩衝區, 則可能會受到緩衝區溢位的影響, 假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="8a90e-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a90e-135">範例</span><span class="sxs-lookup"><span data-stu-id="8a90e-135">Example</span></span>  
 <span data-ttu-id="8a90e-136">下列範例顯示如何為應用程式啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="8a90e-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="8a90e-137">支援於</span><span class="sxs-lookup"><span data-stu-id="8a90e-137">Supported in</span></span>

<span data-ttu-id="8a90e-138">.NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="8a90e-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="8a90e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a90e-139">See also</span></span>

- [<span data-ttu-id="8a90e-140">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="8a90e-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8a90e-141">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="8a90e-141">Configuration File Schema</span></span>](../index.md)
