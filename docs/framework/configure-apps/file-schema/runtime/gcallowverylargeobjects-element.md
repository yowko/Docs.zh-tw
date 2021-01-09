---
title: gcAllowVeryLargeObjects 項目
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 1e54b0780ffb5bbe81ab1be2b376ff7a038ee05c
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058125"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="9ecfa-102">\<gcAllowVeryLargeObjects> 項目</span><span class="sxs-lookup"><span data-stu-id="9ecfa-102">\<gcAllowVeryLargeObjects> element</span></span>

<span data-ttu-id="9ecfa-103">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="9ecfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ecfa-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects enabled="true|false" />  
```  
  
## <a name="attributes"></a><span data-ttu-id="9ecfa-105">屬性</span><span class="sxs-lookup"><span data-stu-id="9ecfa-105">Attributes</span></span>
  
|<span data-ttu-id="9ecfa-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9ecfa-106">Attribute</span></span>|<span data-ttu-id="9ecfa-107">描述</span><span class="sxs-lookup"><span data-stu-id="9ecfa-107">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9ecfa-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-108">Required attribute.</span></span><br /><br /> <span data-ttu-id="9ecfa-109">指定是否在64位平臺上啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-109">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="9ecfa-110">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="9ecfa-110">enabled attribute</span></span>  
  
|<span data-ttu-id="9ecfa-111">值</span><span class="sxs-lookup"><span data-stu-id="9ecfa-111">Value</span></span>|<span data-ttu-id="9ecfa-112">描述</span><span class="sxs-lookup"><span data-stu-id="9ecfa-112">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9ecfa-113">未啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-113">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="9ecfa-114">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-114">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9ecfa-115">在64位平臺上，已啟用大小總計大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-115">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="9ecfa-116">子元素</span><span class="sxs-lookup"><span data-stu-id="9ecfa-116">Child elements</span></span>  

<span data-ttu-id="9ecfa-117">無。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-117">None.</span></span>  
  
## <a name="parent-elements"></a><span data-ttu-id="9ecfa-118">父元素</span><span class="sxs-lookup"><span data-stu-id="9ecfa-118">Parent elements</span></span>
  
|<span data-ttu-id="9ecfa-119">元素</span><span class="sxs-lookup"><span data-stu-id="9ecfa-119">Element</span></span>|<span data-ttu-id="9ecfa-120">描述</span><span class="sxs-lookup"><span data-stu-id="9ecfa-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9ecfa-121">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9ecfa-122">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-122">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ecfa-123">備註</span><span class="sxs-lookup"><span data-stu-id="9ecfa-123">Remarks</span></span>  

 <span data-ttu-id="9ecfa-124">在您的應用程式佈建檔中使用此元素，可啟用大小超過 2 GB 的陣列，但不會變更物件大小或陣列大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="9ecfa-124">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="9ecfa-125">陣列中的元素數目上限為 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-125">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="9ecfa-126">任何單一維度的大小上限為 2147483591 (位元組陣列的 0x7FFFFFC7) 和單一位元組結構的陣列，以及包含其他類型之陣列的 2146435071 (0X7FEFFFFF) 。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-126">The maximum size in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for arrays containing other types.</span></span>  
  
- <span data-ttu-id="9ecfa-127">字串和其他非陣列物件的大小上限不變。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-127">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9ecfa-128">啟用這項功能之前，請確定您的應用程式不包含不安全的程式碼，該程式碼會假設所有陣列的大小都小於 2 GB。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-128">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="9ecfa-129">例如，使用陣列做為緩衝區的 unsafe 程式碼可能會受到緩衝區溢位的影響，因為假設陣列不會超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-129">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it's written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecfa-130">範例</span><span class="sxs-lookup"><span data-stu-id="9ecfa-130">Example</span></span>  

 <span data-ttu-id="9ecfa-131">下列範例顯示如何為應用程式啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="9ecfa-131">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="9ecfa-132">支援於</span><span class="sxs-lookup"><span data-stu-id="9ecfa-132">Supported in</span></span>

<span data-ttu-id="9ecfa-133">.NET Framework 4.5 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9ecfa-133">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="9ecfa-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ecfa-134">See also</span></span>

- [<span data-ttu-id="9ecfa-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9ecfa-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9ecfa-136">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="9ecfa-136">Configuration File Schema</span></span>](../index.md)
