---
title: <UseSmallInternalThreadStacks> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 2fd776ce8605e6dcf288dcb3852ded16638a1873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114928"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="39c13-102">\<UseSmallInternalThreadStacks > 元素</span><span class="sxs-lookup"><span data-stu-id="39c13-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="39c13-103">要求 common language runtime （CLR）在建立內部使用的特定執行緒時，指定明確的堆疊大小來減少記憶體使用，而不是使用這些執行緒的預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
<span data-ttu-id="39c13-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39c13-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39c13-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="39c13-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="39c13-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseSmallInternalThreadStacks >**</span><span class="sxs-lookup"><span data-stu-id="39c13-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c13-107">語法</span><span class="sxs-lookup"><span data-stu-id="39c13-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39c13-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39c13-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39c13-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39c13-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39c13-110">屬性</span><span class="sxs-lookup"><span data-stu-id="39c13-110">Attributes</span></span>  
  
|<span data-ttu-id="39c13-111">屬性</span><span class="sxs-lookup"><span data-stu-id="39c13-111">Attribute</span></span>|<span data-ttu-id="39c13-112">描述</span><span class="sxs-lookup"><span data-stu-id="39c13-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39c13-113">enabled</span><span class="sxs-lookup"><span data-stu-id="39c13-113">enabled</span></span>|<span data-ttu-id="39c13-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="39c13-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="39c13-115">指定在建立內部使用的特定執行緒時，是否要要求 CLR 使用明確堆疊大小，而不是預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="39c13-116">明確堆疊大小小於 1 MB 的預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="39c13-117">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="39c13-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="39c13-118">值</span><span class="sxs-lookup"><span data-stu-id="39c13-118">Value</span></span>|<span data-ttu-id="39c13-119">描述</span><span class="sxs-lookup"><span data-stu-id="39c13-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39c13-120">true</span><span class="sxs-lookup"><span data-stu-id="39c13-120">true</span></span>|<span data-ttu-id="39c13-121">要求明確堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="39c13-122">False</span><span class="sxs-lookup"><span data-stu-id="39c13-122">false</span></span>|<span data-ttu-id="39c13-123">使用預設堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-123">Use the default stack size.</span></span> <span data-ttu-id="39c13-124">這是 .NET Framework 4 的預設值。</span><span class="sxs-lookup"><span data-stu-id="39c13-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39c13-125">子項目</span><span class="sxs-lookup"><span data-stu-id="39c13-125">Child Elements</span></span>  
 <span data-ttu-id="39c13-126">無。</span><span class="sxs-lookup"><span data-stu-id="39c13-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39c13-127">父項目</span><span class="sxs-lookup"><span data-stu-id="39c13-127">Parent Elements</span></span>  
  
|<span data-ttu-id="39c13-128">項目</span><span class="sxs-lookup"><span data-stu-id="39c13-128">Element</span></span>|<span data-ttu-id="39c13-129">描述</span><span class="sxs-lookup"><span data-stu-id="39c13-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39c13-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="39c13-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="39c13-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="39c13-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c13-132">備註</span><span class="sxs-lookup"><span data-stu-id="39c13-132">Remarks</span></span>  
 <span data-ttu-id="39c13-133">這個設定元素是用來要求在進程中減少使用的虛擬記憶體，因為 CLR 針對其內部執行緒使用的明確執行緒大小，如果接受要求，則小於預設大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="39c13-134">此設定元素是對 CLR 的要求，而不是絕對需求。</span><span class="sxs-lookup"><span data-stu-id="39c13-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="39c13-135">在 .NET Framework 4 中，要求僅適用于 x86 架構。</span><span class="sxs-lookup"><span data-stu-id="39c13-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="39c13-136">這個元素可能會在未來的 CLR 版本中完全忽略，或由一律用於所選內部執行緒的明確堆疊大小來取代。</span><span class="sxs-lookup"><span data-stu-id="39c13-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="39c13-137">指定此設定元素會在 CLR 接受要求時，將可靠性用於較小的虛擬記憶體使用，因為較小的堆疊大小可能會使堆疊溢位更有可能。</span><span class="sxs-lookup"><span data-stu-id="39c13-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39c13-138">範例</span><span class="sxs-lookup"><span data-stu-id="39c13-138">Example</span></span>  
 <span data-ttu-id="39c13-139">下列範例示範如何要求 CLR 針對它在內部使用的特定執行緒使用明確堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="39c13-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39c13-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="39c13-140">See also</span></span>

- [<span data-ttu-id="39c13-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="39c13-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="39c13-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="39c13-142">Configuration File Schema</span></span>](../index.md)
