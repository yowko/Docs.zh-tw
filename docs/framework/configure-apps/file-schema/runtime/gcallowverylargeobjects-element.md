---
title: <gcAllowVeryLargeObjects> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 78a42596aae6c3ea0d94ac759d11ed52d0ace539
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178225"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="e1395-102">\<gcAllowVeryLargeObjects> 項目</span><span class="sxs-lookup"><span data-stu-id="e1395-102">\<gcAllowVeryLargeObjects> Element</span></span>

<span data-ttu-id="e1395-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1395-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="e1395-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1395-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1395-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e1395-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e1395-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e1395-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1395-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e1395-107">Attributes</span></span>  
  
|<span data-ttu-id="e1395-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e1395-108">Attribute</span></span>|<span data-ttu-id="e1395-109">描述</span><span class="sxs-lookup"><span data-stu-id="e1395-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e1395-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e1395-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="e1395-111">指定是否在64位平臺上啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1395-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e1395-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="e1395-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="e1395-113">值</span><span class="sxs-lookup"><span data-stu-id="e1395-113">Value</span></span>|<span data-ttu-id="e1395-114">描述</span><span class="sxs-lookup"><span data-stu-id="e1395-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e1395-115">未啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1395-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="e1395-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="e1395-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="e1395-117">在64位平臺上，已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1395-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1395-118">子元素</span><span class="sxs-lookup"><span data-stu-id="e1395-118">Child Elements</span></span>  

 <span data-ttu-id="e1395-119">無。</span><span class="sxs-lookup"><span data-stu-id="e1395-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1395-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e1395-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1395-121">項目</span><span class="sxs-lookup"><span data-stu-id="e1395-121">Element</span></span>|<span data-ttu-id="e1395-122">描述</span><span class="sxs-lookup"><span data-stu-id="e1395-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e1395-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e1395-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e1395-124">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="e1395-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1395-125">備註</span><span class="sxs-lookup"><span data-stu-id="e1395-125">Remarks</span></span>  

 <span data-ttu-id="e1395-126">在您的應用程式佈建檔中使用此元素，可啟用大小超過 2 GB 的陣列，但不會變更物件大小或陣列大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="e1395-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="e1395-127">陣列中的元素數目上限為 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e1395-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="e1395-128">任何單一維度中的最大索引為 2147483591 (位元組陣列的 0x7FFFFFC7) 和單一位元組結構的陣列，以及適用于其他類型的 2146435071 (0X7FEFFFFF) 。</span><span class="sxs-lookup"><span data-stu-id="e1395-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="e1395-129">字串和其他非陣列物件的大小上限不變。</span><span class="sxs-lookup"><span data-stu-id="e1395-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e1395-130">啟用這項功能之前，請確定您的應用程式不包含不安全的程式碼，該程式碼會假設所有陣列的大小都小於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="e1395-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="e1395-131">例如，使用陣列做為緩衝區的 unsafe 程式碼可能會受到緩衝區溢位的影響，因為假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="e1395-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1395-132">範例</span><span class="sxs-lookup"><span data-stu-id="e1395-132">Example</span></span>  

 <span data-ttu-id="e1395-133">下列範例顯示如何為應用程式啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="e1395-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="e1395-134">支援於</span><span class="sxs-lookup"><span data-stu-id="e1395-134">Supported in</span></span>

<span data-ttu-id="e1395-135">.NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="e1395-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="e1395-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1395-136">See also</span></span>

- [<span data-ttu-id="e1395-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e1395-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e1395-138">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="e1395-138">Configuration File Schema</span></span>](../index.md)
