---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9833d768b84faaf6e1dcf8c9cb8b00b92adc3d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144818"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="dc03b-102">\<UseSmallInternalThreadStacks > 項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="dc03b-103">藉由指定明確的堆疊大小，它會建立它會在內部使用，而不是使用預設堆疊大小為這些執行緒進行特定執行緒時，使用 common language runtime (CLR)，減少記憶體的要求。</span><span class="sxs-lookup"><span data-stu-id="dc03b-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="dc03b-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-104">\<configuration> Element</span></span>  
<span data-ttu-id="dc03b-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-105">\<runtime> Element</span></span>  
<span data-ttu-id="dc03b-106">\<UseSmallInternalThreadStacks > 項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc03b-107">語法</span><span class="sxs-lookup"><span data-stu-id="dc03b-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc03b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dc03b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dc03b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc03b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="dc03b-110">Attributes</span></span>  
  
|<span data-ttu-id="dc03b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dc03b-111">Attribute</span></span>|<span data-ttu-id="dc03b-112">描述</span><span class="sxs-lookup"><span data-stu-id="dc03b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc03b-113">enabled</span><span class="sxs-lookup"><span data-stu-id="dc03b-113">enabled</span></span>|<span data-ttu-id="dc03b-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="dc03b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="dc03b-115">指定是否要要求 CLR 使用明確的堆疊大小，而不是預設的堆疊大小時它會建立內部使用的特定執行緒。</span><span class="sxs-lookup"><span data-stu-id="dc03b-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="dc03b-116">明確的堆疊大小是小於 1 MB 的預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="dc03b-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dc03b-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="dc03b-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="dc03b-118">值</span><span class="sxs-lookup"><span data-stu-id="dc03b-118">Value</span></span>|<span data-ttu-id="dc03b-119">描述</span><span class="sxs-lookup"><span data-stu-id="dc03b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dc03b-120">true</span><span class="sxs-lookup"><span data-stu-id="dc03b-120">true</span></span>|<span data-ttu-id="dc03b-121">要求明確的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="dc03b-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="dc03b-122">False</span><span class="sxs-lookup"><span data-stu-id="dc03b-122">false</span></span>|<span data-ttu-id="dc03b-123">使用預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="dc03b-123">Use the default stack size.</span></span> <span data-ttu-id="dc03b-124">這是預設值[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dc03b-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc03b-125">子元素</span><span class="sxs-lookup"><span data-stu-id="dc03b-125">Child Elements</span></span>  
 <span data-ttu-id="dc03b-126">無。</span><span class="sxs-lookup"><span data-stu-id="dc03b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc03b-127">父項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="dc03b-128">項目</span><span class="sxs-lookup"><span data-stu-id="dc03b-128">Element</span></span>|<span data-ttu-id="dc03b-129">描述</span><span class="sxs-lookup"><span data-stu-id="dc03b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dc03b-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dc03b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dc03b-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc03b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc03b-132">備註</span><span class="sxs-lookup"><span data-stu-id="dc03b-132">Remarks</span></span>  
 <span data-ttu-id="dc03b-133">這個組態項目用來要求縮減的虛擬記憶體的使用，在處理序中，因為如果遵循，則要求，CLR 會使用其內部的執行緒，則明確的執行緒大小是小於預設大小。</span><span class="sxs-lookup"><span data-stu-id="dc03b-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc03b-134">這個組態項目是 CLR，而不是絕對必要的需求的要求。</span><span class="sxs-lookup"><span data-stu-id="dc03b-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="dc03b-135">在  [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，要求會接受僅適用於 x86 架構。</span><span class="sxs-lookup"><span data-stu-id="dc03b-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="dc03b-136">這個項目可能會完全忽略未來的 CLR 版本中，或以一律用於進行選取的內部執行緒的明確的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="dc03b-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="dc03b-137">指定這個組態項目往來可靠性較小的虛擬記憶體使用，是否 CLR 會接受要求，因為較小的堆疊大小可能會無法使堆疊更可能溢位。</span><span class="sxs-lookup"><span data-stu-id="dc03b-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc03b-138">範例</span><span class="sxs-lookup"><span data-stu-id="dc03b-138">Example</span></span>  
 <span data-ttu-id="dc03b-139">下列範例示範如何要求 CLR 使用明確堆疊調整某些大小它會在內部使用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="dc03b-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc03b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc03b-140">See also</span></span>

- [<span data-ttu-id="dc03b-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="dc03b-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="dc03b-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="dc03b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
