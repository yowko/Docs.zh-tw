---
title: <ThrowUnobservedTaskExceptions> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b47c4d07fc0ee0cdaf53fe3c8199fb37dcb6c1b1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377894"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="efbd3-102">\<ThrowUnobservedTaskExceptions > 項目</span><span class="sxs-lookup"><span data-stu-id="efbd3-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="efbd3-103">指定未處理的工作例外狀況是否應終止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="efbd3-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="efbd3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="efbd3-104">\<configuration></span></span>  
<span data-ttu-id="efbd3-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="efbd3-105">\<runtime></span></span>  
<span data-ttu-id="efbd3-106">\<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="efbd3-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efbd3-107">語法</span><span class="sxs-lookup"><span data-stu-id="efbd3-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efbd3-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="efbd3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efbd3-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="efbd3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efbd3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="efbd3-110">Attributes</span></span>  
  
|<span data-ttu-id="efbd3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="efbd3-111">Attribute</span></span>|<span data-ttu-id="efbd3-112">描述</span><span class="sxs-lookup"><span data-stu-id="efbd3-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="efbd3-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="efbd3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="efbd3-114">指定未處理的工作例外狀況是否終止執行中處理序。</span><span class="sxs-lookup"><span data-stu-id="efbd3-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="efbd3-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="efbd3-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="efbd3-116">值</span><span class="sxs-lookup"><span data-stu-id="efbd3-116">Value</span></span>|<span data-ttu-id="efbd3-117">描述</span><span class="sxs-lookup"><span data-stu-id="efbd3-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="efbd3-118">不會終止執行中處理序例外狀況未處理的工作。</span><span class="sxs-lookup"><span data-stu-id="efbd3-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="efbd3-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="efbd3-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="efbd3-120">終止執行中處理序例外狀況未處理的工作。</span><span class="sxs-lookup"><span data-stu-id="efbd3-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efbd3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="efbd3-121">Child Elements</span></span>  
 <span data-ttu-id="efbd3-122">無。</span><span class="sxs-lookup"><span data-stu-id="efbd3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efbd3-123">父項目</span><span class="sxs-lookup"><span data-stu-id="efbd3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="efbd3-124">項目</span><span class="sxs-lookup"><span data-stu-id="efbd3-124">Element</span></span>|<span data-ttu-id="efbd3-125">描述</span><span class="sxs-lookup"><span data-stu-id="efbd3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="efbd3-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="efbd3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="efbd3-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="efbd3-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="efbd3-128">備註</span><span class="sxs-lookup"><span data-stu-id="efbd3-128">Remarks</span></span>  
 <span data-ttu-id="efbd3-129">如果例外狀況相關聯<xref:System.Threading.Tasks.Task>尚未發現，沒有任何<xref:System.Threading.Tasks.Task.Wait%2A>未附加作業，父代，而<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>屬性未讀取的工作例外狀況會被視為未觀察到。</span><span class="sxs-lookup"><span data-stu-id="efbd3-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="efbd3-130">在  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，依預設，如果<xref:System.Threading.Tasks.Task>具有未觀察到例外狀況是記憶體回收，完成項會擲回例外狀況，並終止處理序。</span><span class="sxs-lookup"><span data-stu-id="efbd3-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="efbd3-131">終止處理序取決於記憶體回收行程和終結的時機。</span><span class="sxs-lookup"><span data-stu-id="efbd3-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="efbd3-132">若要簡化開發人員撰寫工作為基礎的非同步程式碼，.NET Framework 4.5 中變更此預設行為未觀察到的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="efbd3-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="efbd3-133">未觀察到的例外狀況，仍有導致<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>事件引發，但根據預設，此程序不會終止。</span><span class="sxs-lookup"><span data-stu-id="efbd3-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="efbd3-134">相反地，引發事件，不論事件處理常式是否會觀察到例外狀況之後，會忽略例外狀況。</span><span class="sxs-lookup"><span data-stu-id="efbd3-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="efbd3-135">在.NET Framework 4.5 中，您可以使用[ \<ThrowUnobservedTaskExceptions > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)應用程式組態檔中啟用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]擲回例外狀況的行為。</span><span class="sxs-lookup"><span data-stu-id="efbd3-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="efbd3-136">您也可以指定的例外狀況行為中的下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="efbd3-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="efbd3-137">藉由設定環境變數`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。</span><span class="sxs-lookup"><span data-stu-id="efbd3-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="efbd3-138">藉由設定登錄 DWORD 值 ThrowUnobservedTaskExceptions = 1 在 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="efbd3-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efbd3-139">範例</span><span class="sxs-lookup"><span data-stu-id="efbd3-139">Example</span></span>  
 <span data-ttu-id="efbd3-140">下列範例示範如何啟用擲回的例外狀況，在工作中使用應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="efbd3-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="efbd3-141">範例</span><span class="sxs-lookup"><span data-stu-id="efbd3-141">Example</span></span>  
 <span data-ttu-id="efbd3-142">下列範例會示範如何從工作擲回未觀察到的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="efbd3-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="efbd3-143">為發行的程式正常運作，必須執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="efbd3-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="efbd3-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efbd3-144">See also</span></span>

- [<span data-ttu-id="efbd3-145">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="efbd3-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="efbd3-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="efbd3-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
