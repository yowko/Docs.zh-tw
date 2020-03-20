---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154123"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="23d64-102">\<gcAllow非常大的物件>元素</span><span class="sxs-lookup"><span data-stu-id="23d64-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="23d64-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="23d64-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="23d64-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="23d64-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="23d64-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="23d64-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="23d64-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllow 非常大的物件>**</span><span class="sxs-lookup"><span data-stu-id="23d64-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d64-107">語法</span><span class="sxs-lookup"><span data-stu-id="23d64-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23d64-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="23d64-108">Attributes and Elements</span></span>  
 <span data-ttu-id="23d64-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="23d64-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23d64-110">屬性</span><span class="sxs-lookup"><span data-stu-id="23d64-110">Attributes</span></span>  
  
|<span data-ttu-id="23d64-111">屬性</span><span class="sxs-lookup"><span data-stu-id="23d64-111">Attribute</span></span>|<span data-ttu-id="23d64-112">描述</span><span class="sxs-lookup"><span data-stu-id="23d64-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="23d64-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="23d64-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="23d64-114">指定是否在 64 位平臺上啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="23d64-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="23d64-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="23d64-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="23d64-116">值</span><span class="sxs-lookup"><span data-stu-id="23d64-116">Value</span></span>|<span data-ttu-id="23d64-117">描述</span><span class="sxs-lookup"><span data-stu-id="23d64-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="23d64-118">未啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="23d64-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="23d64-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="23d64-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="23d64-120">在 64 位平臺上啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="23d64-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23d64-121">子元素</span><span class="sxs-lookup"><span data-stu-id="23d64-121">Child Elements</span></span>  
 <span data-ttu-id="23d64-122">無。</span><span class="sxs-lookup"><span data-stu-id="23d64-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23d64-123">父項目</span><span class="sxs-lookup"><span data-stu-id="23d64-123">Parent Elements</span></span>  
  
|<span data-ttu-id="23d64-124">元素</span><span class="sxs-lookup"><span data-stu-id="23d64-124">Element</span></span>|<span data-ttu-id="23d64-125">描述</span><span class="sxs-lookup"><span data-stu-id="23d64-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="23d64-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="23d64-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="23d64-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="23d64-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d64-128">備註</span><span class="sxs-lookup"><span data-stu-id="23d64-128">Remarks</span></span>  
 <span data-ttu-id="23d64-129">在應用程式佈建檔中使用此元素可啟用大小大於 2 GB 但不會改變對物件大小或陣列大小的其他限制的陣列：</span><span class="sxs-lookup"><span data-stu-id="23d64-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="23d64-130">陣列中的最大元素數為<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="23d64-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="23d64-131">對於單位元組結構的位元組陣列和陣列，任何單個維度中的最大索引為 2，147，483，591 （0x7FFFFFC7），其他類型的為 2，146，435，071 （0X7FFFFF）。</span><span class="sxs-lookup"><span data-stu-id="23d64-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="23d64-132">字串和其他非陣列物件的最大大小保持不變。</span><span class="sxs-lookup"><span data-stu-id="23d64-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="23d64-133">在啟用此功能之前，請確保應用程式不包含假定所有陣列大小小於 2 GB 的不安全代碼。</span><span class="sxs-lookup"><span data-stu-id="23d64-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="23d64-134">例如，如果使用陣列作為緩衝區的不安全代碼，如果編寫時假定陣列不會超過 2 GB，則很容易出現緩衝區溢位。</span><span class="sxs-lookup"><span data-stu-id="23d64-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23d64-135">範例</span><span class="sxs-lookup"><span data-stu-id="23d64-135">Example</span></span>  
 <span data-ttu-id="23d64-136">下面的示例演示如何為應用程式啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="23d64-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="23d64-137">支援於</span><span class="sxs-lookup"><span data-stu-id="23d64-137">Supported in</span></span>

<span data-ttu-id="23d64-138">.NET 框架 4.5 及更高版本</span><span class="sxs-lookup"><span data-stu-id="23d64-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="23d64-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23d64-139">See also</span></span>

- [<span data-ttu-id="23d64-140">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="23d64-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="23d64-141">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="23d64-141">Configuration File Schema</span></span>](../index.md)
