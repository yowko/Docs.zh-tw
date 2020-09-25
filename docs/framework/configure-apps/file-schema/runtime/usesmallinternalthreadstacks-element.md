---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 4917b47e9e8196eabe691f74531d12308ef80311
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174078"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="bf5bb-102">\<UseSmallInternalThreadStacks> 項目</span><span class="sxs-lookup"><span data-stu-id="bf5bb-102">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="bf5bb-103">要求 common language runtime (CLR) 在建立它在內部使用的特定執行緒時，指定明確的堆疊大小來減少記憶體使用，而不是使用這些執行緒的預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="bf5bb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bf5bb-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf5bb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bf5bb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bf5bb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf5bb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bf5bb-107">Attributes</span></span>  
  
|<span data-ttu-id="bf5bb-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bf5bb-108">Attribute</span></span>|<span data-ttu-id="bf5bb-109">描述</span><span class="sxs-lookup"><span data-stu-id="bf5bb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf5bb-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="bf5bb-110">enabled</span></span>|<span data-ttu-id="bf5bb-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf5bb-112">指定當 CLR 建立在內部使用的特定執行緒時，是否要求 CLR 使用明確堆疊大小，而不是預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="bf5bb-113">明確堆疊大小小於預設堆疊大小 1 MB。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf5bb-114">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="bf5bb-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf5bb-115">值</span><span class="sxs-lookup"><span data-stu-id="bf5bb-115">Value</span></span>|<span data-ttu-id="bf5bb-116">描述</span><span class="sxs-lookup"><span data-stu-id="bf5bb-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf5bb-117">true</span><span class="sxs-lookup"><span data-stu-id="bf5bb-117">true</span></span>|<span data-ttu-id="bf5bb-118">要求明確的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="bf5bb-119">false</span><span class="sxs-lookup"><span data-stu-id="bf5bb-119">false</span></span>|<span data-ttu-id="bf5bb-120">使用預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-120">Use the default stack size.</span></span> <span data-ttu-id="bf5bb-121">這是 .NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf5bb-122">子元素</span><span class="sxs-lookup"><span data-stu-id="bf5bb-122">Child Elements</span></span>  

 <span data-ttu-id="bf5bb-123">無。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf5bb-124">父項目</span><span class="sxs-lookup"><span data-stu-id="bf5bb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bf5bb-125">項目</span><span class="sxs-lookup"><span data-stu-id="bf5bb-125">Element</span></span>|<span data-ttu-id="bf5bb-126">描述</span><span class="sxs-lookup"><span data-stu-id="bf5bb-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf5bb-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf5bb-128">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf5bb-129">備註</span><span class="sxs-lookup"><span data-stu-id="bf5bb-129">Remarks</span></span>  

 <span data-ttu-id="bf5bb-130">這個設定元素可用來要求減少在進程中使用的虛擬記憶體，因為 CLR 針對其內部執行緒使用的明確執行緒大小（如果接受要求的話）小於預設大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf5bb-131">這個設定元素是對 CLR 的要求，而不是絕對需求。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="bf5bb-132">在 .NET Framework 4 中，只會針對 x86 架構接受要求。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="bf5bb-133">此元素可能會在未來的 CLR 版本中完全被忽略，或由一律用於所選取內部執行緒的明確堆疊大小所取代。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="bf5bb-134">如果 CLR 接受要求，則指定此設定專案會針對較小的虛擬記憶體使用量來提高可靠性，因為較小的堆疊大小可能會讓堆疊溢位更有可能。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf5bb-135">範例</span><span class="sxs-lookup"><span data-stu-id="bf5bb-135">Example</span></span>  

 <span data-ttu-id="bf5bb-136">下列範例示範如何要求 CLR 針對它在內部使用的特定執行緒，使用明確的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="bf5bb-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf5bb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf5bb-137">See also</span></span>

- [<span data-ttu-id="bf5bb-138">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bf5bb-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf5bb-139">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="bf5bb-139">Configuration File Schema</span></span>](../index.md)
