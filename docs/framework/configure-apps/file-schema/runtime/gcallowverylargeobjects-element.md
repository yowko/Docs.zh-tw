---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154123"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="a7862-102">\<gcAllowVeryLargeObjects> 項目</span><span class="sxs-lookup"><span data-stu-id="a7862-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="a7862-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a7862-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="a7862-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7862-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7862-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7862-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a7862-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a7862-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7862-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a7862-107">Attributes</span></span>  
  
|<span data-ttu-id="a7862-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a7862-108">Attribute</span></span>|<span data-ttu-id="a7862-109">描述</span><span class="sxs-lookup"><span data-stu-id="a7862-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a7862-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a7862-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a7862-111">指定在64位平臺上，是否已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a7862-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a7862-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="a7862-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="a7862-113">值</span><span class="sxs-lookup"><span data-stu-id="a7862-113">Value</span></span>|<span data-ttu-id="a7862-114">描述</span><span class="sxs-lookup"><span data-stu-id="a7862-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a7862-115">未啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a7862-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="a7862-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="a7862-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a7862-117">64位平臺上已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a7862-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7862-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a7862-118">Child Elements</span></span>  
 <span data-ttu-id="a7862-119">無。</span><span class="sxs-lookup"><span data-stu-id="a7862-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7862-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a7862-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a7862-121">元素</span><span class="sxs-lookup"><span data-stu-id="a7862-121">Element</span></span>|<span data-ttu-id="a7862-122">描述</span><span class="sxs-lookup"><span data-stu-id="a7862-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a7862-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a7862-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a7862-124">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="a7862-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7862-125">備註</span><span class="sxs-lookup"><span data-stu-id="a7862-125">Remarks</span></span>  
 <span data-ttu-id="a7862-126">在您的應用程式佈建檔中使用此元素，可讓大小大於 2 GB 的陣列，但不會變更物件大小或陣列大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="a7862-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="a7862-127">陣列中的元素數目上限為 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a7862-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="a7862-128">任何單一維度中的最大索引為2147483591（0x7FFFFFC7），適用于位元組陣列和單一位元組結構的陣列，以及適用于其他類型的2146435071（0X7FEFFFFF）。</span><span class="sxs-lookup"><span data-stu-id="a7862-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="a7862-129">字串和其他非陣列物件的大小上限不變。</span><span class="sxs-lookup"><span data-stu-id="a7862-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a7862-130">啟用這項功能之前，請確定您的應用程式不包含不安全的程式碼，其假設所有的陣列大小都小於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="a7862-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="a7862-131">例如，如果不安全的程式碼是以陣列做為緩衝區，則可能會受到緩衝區溢位的影響，假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="a7862-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7862-132">範例</span><span class="sxs-lookup"><span data-stu-id="a7862-132">Example</span></span>  
 <span data-ttu-id="a7862-133">下列範例顯示如何為應用程式啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="a7862-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="a7862-134">支援於</span><span class="sxs-lookup"><span data-stu-id="a7862-134">Supported in</span></span>

<span data-ttu-id="a7862-135">.NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a7862-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="a7862-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7862-136">See also</span></span>

- [<span data-ttu-id="a7862-137">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="a7862-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a7862-138">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a7862-138">Configuration File Schema</span></span>](../index.md)
