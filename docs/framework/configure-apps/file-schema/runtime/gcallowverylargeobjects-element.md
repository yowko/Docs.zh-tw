---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 70c60461f3ddd6bdabd151f60c7bc81eef18e650
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629465"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="74716-102">\<Gcallowverylargeobjects> > 元素</span><span class="sxs-lookup"><span data-stu-id="74716-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="74716-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="74716-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="74716-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="74716-104">\<configuration> Element</span></span>  
<span data-ttu-id="74716-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="74716-105">\<runtime> Element</span></span>  
<span data-ttu-id="74716-106">\<Gcallowverylargeobjects> > 元素</span><span class="sxs-lookup"><span data-stu-id="74716-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74716-107">語法</span><span class="sxs-lookup"><span data-stu-id="74716-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74716-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="74716-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74716-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="74716-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74716-110">屬性</span><span class="sxs-lookup"><span data-stu-id="74716-110">Attributes</span></span>  
  
|<span data-ttu-id="74716-111">屬性</span><span class="sxs-lookup"><span data-stu-id="74716-111">Attribute</span></span>|<span data-ttu-id="74716-112">描述</span><span class="sxs-lookup"><span data-stu-id="74716-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="74716-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="74716-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="74716-114">指定在64位平臺上, 是否已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="74716-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="74716-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="74716-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="74716-116">值</span><span class="sxs-lookup"><span data-stu-id="74716-116">Value</span></span>|<span data-ttu-id="74716-117">描述</span><span class="sxs-lookup"><span data-stu-id="74716-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="74716-118">未啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="74716-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="74716-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="74716-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="74716-120">64位平臺上已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="74716-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74716-121">子元素</span><span class="sxs-lookup"><span data-stu-id="74716-121">Child Elements</span></span>  
 <span data-ttu-id="74716-122">無。</span><span class="sxs-lookup"><span data-stu-id="74716-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74716-123">父項目</span><span class="sxs-lookup"><span data-stu-id="74716-123">Parent Elements</span></span>  
  
|<span data-ttu-id="74716-124">項目</span><span class="sxs-lookup"><span data-stu-id="74716-124">Element</span></span>|<span data-ttu-id="74716-125">說明</span><span class="sxs-lookup"><span data-stu-id="74716-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="74716-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="74716-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="74716-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="74716-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74716-128">備註</span><span class="sxs-lookup"><span data-stu-id="74716-128">Remarks</span></span>  
 <span data-ttu-id="74716-129">在您的應用程式佈建檔中使用此元素, 可讓大小大於 2 GB 的陣列, 但不會變更物件大小或陣列大小的其他限制:</span><span class="sxs-lookup"><span data-stu-id="74716-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="74716-130">陣列中的元素數目上限為<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="74716-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="74716-131">任何單一維度中的最大索引為 2147483591 (0x7FFFFFC7), 適用于位元組陣列和單一位元組結構的陣列, 以及適用于其他類型的 2146435071 (0X7FEFFFFF)。</span><span class="sxs-lookup"><span data-stu-id="74716-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="74716-132">字串和其他非陣列物件的大小上限不變。</span><span class="sxs-lookup"><span data-stu-id="74716-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="74716-133">啟用這項功能之前, 請確定您的應用程式不包含不安全的程式碼, 其假設所有的陣列大小都小於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="74716-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="74716-134">例如, 如果不安全的程式碼是以陣列做為緩衝區, 則可能會受到緩衝區溢位的影響, 假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="74716-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74716-135">範例</span><span class="sxs-lookup"><span data-stu-id="74716-135">Example</span></span>  
 <span data-ttu-id="74716-136">下列範例顯示如何為應用程式啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="74716-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="74716-137">支援於</span><span class="sxs-lookup"><span data-stu-id="74716-137">Supported in</span></span>

<span data-ttu-id="74716-138">.NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="74716-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="74716-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74716-139">See also</span></span>

- [<span data-ttu-id="74716-140">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="74716-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="74716-141">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="74716-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
