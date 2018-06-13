---
title: '&lt;ThrowUnobservedTaskExceptions&gt;項目'
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
ms.openlocfilehash: 3f72bedbaaf0b15ade7ff6b7b8c3edcdfd3fda6d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749422"
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a><span data-ttu-id="d84cf-102">&lt;ThrowUnobservedTaskExceptions&gt;項目</span><span class="sxs-lookup"><span data-stu-id="d84cf-102">&lt;ThrowUnobservedTaskExceptions&gt; Element</span></span>
<span data-ttu-id="d84cf-103">指定未處理的工作例外狀況是否應終止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="d84cf-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
 <span data-ttu-id="d84cf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d84cf-104">\<configuration></span></span>  
<span data-ttu-id="d84cf-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="d84cf-105">\<runtime></span></span>  
<span data-ttu-id="d84cf-106">\<ThrowUnobservedTaskExceptions ></span><span class="sxs-lookup"><span data-stu-id="d84cf-106">\<ThrowUnobservedTaskExceptions></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84cf-107">語法</span><span class="sxs-lookup"><span data-stu-id="d84cf-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d84cf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d84cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d84cf-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d84cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d84cf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d84cf-110">Attributes</span></span>  
  
|<span data-ttu-id="d84cf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d84cf-111">Attribute</span></span>|<span data-ttu-id="d84cf-112">描述</span><span class="sxs-lookup"><span data-stu-id="d84cf-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d84cf-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d84cf-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d84cf-114">指定的例外狀況處理的工作是否終止執行中處理序。</span><span class="sxs-lookup"><span data-stu-id="d84cf-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d84cf-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="d84cf-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d84cf-116">值</span><span class="sxs-lookup"><span data-stu-id="d84cf-116">Value</span></span>|<span data-ttu-id="d84cf-117">描述</span><span class="sxs-lookup"><span data-stu-id="d84cf-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d84cf-118">不會終止例外狀況處理的工作執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="d84cf-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="d84cf-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="d84cf-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d84cf-120">終止執行中處理序例外狀況處理的工作。</span><span class="sxs-lookup"><span data-stu-id="d84cf-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d84cf-121">子項目</span><span class="sxs-lookup"><span data-stu-id="d84cf-121">Child Elements</span></span>  
 <span data-ttu-id="d84cf-122">無。</span><span class="sxs-lookup"><span data-stu-id="d84cf-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d84cf-123">父項目</span><span class="sxs-lookup"><span data-stu-id="d84cf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d84cf-124">項目</span><span class="sxs-lookup"><span data-stu-id="d84cf-124">Element</span></span>|<span data-ttu-id="d84cf-125">描述</span><span class="sxs-lookup"><span data-stu-id="d84cf-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d84cf-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="d84cf-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d84cf-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="d84cf-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="d84cf-128">備註</span><span class="sxs-lookup"><span data-stu-id="d84cf-128">Remarks</span></span>  
 <span data-ttu-id="d84cf-129">如果相關聯的例外狀況<xref:System.Threading.Tasks.Task>發現，沒有任何<xref:System.Threading.Tasks.Task.Wait%2A>未連接父代的作業，而<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>屬性未讀取的工作例外狀況會被視為未觀察到。</span><span class="sxs-lookup"><span data-stu-id="d84cf-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="d84cf-130">在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，依預設，如果<xref:System.Threading.Tasks.Task>具有未觀察到的例外是記憶體回收中，完成項擲回例外狀況和終止處理序。</span><span class="sxs-lookup"><span data-stu-id="d84cf-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="d84cf-131">終止處理序取決於記憶體回收和最終處理的時機。</span><span class="sxs-lookup"><span data-stu-id="d84cf-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="d84cf-132">若要簡化開發人員撰寫非同步程式碼，根據工作，[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]變成未觀察到的例外狀況的這個預設行為。</span><span class="sxs-lookup"><span data-stu-id="d84cf-132">To make it easier for developers to write asynchronous code based on tasks, the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="d84cf-133">未觀察到的例外狀況，仍然會使<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>會引發事件，但根據預設，處理程序不會終止。</span><span class="sxs-lookup"><span data-stu-id="d84cf-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="d84cf-134">相反地之後會引發事件，不論是否事件處理常式會觀察到的例外狀況,，則會忽略例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d84cf-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="d84cf-135">在[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]，您可以使用[ \<ThrowUnobservedTaskExceptions > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)應用程式組態檔中啟用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]擲回例外狀況的行為。</span><span class="sxs-lookup"><span data-stu-id="d84cf-135">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], you can use the [\<ThrowUnobservedTaskExceptions> element](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) in an application configuration file to enable the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="d84cf-136">您也可以下列方式之一，指定例外狀況行為：</span><span class="sxs-lookup"><span data-stu-id="d84cf-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
-   <span data-ttu-id="d84cf-137">設定環境變數`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。</span><span class="sxs-lookup"><span data-stu-id="d84cf-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
-   <span data-ttu-id="d84cf-138">藉由設定登錄 DWORD 值 ThrowUnobservedTaskExceptions = 1 中 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d84cf-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d84cf-139">範例</span><span class="sxs-lookup"><span data-stu-id="d84cf-139">Example</span></span>  
 <span data-ttu-id="d84cf-140">下列範例會示範如何啟用擲回的例外狀況，在工作中使用應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="d84cf-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d84cf-141">範例</span><span class="sxs-lookup"><span data-stu-id="d84cf-141">Example</span></span>  
 <span data-ttu-id="d84cf-142">下列範例會示範如何從工作擲回未觀察到的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d84cf-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="d84cf-143">程式碼必須執行以發行的程式正常運作。</span><span class="sxs-lookup"><span data-stu-id="d84cf-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d84cf-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d84cf-144">See Also</span></span>  
 [<span data-ttu-id="d84cf-145">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d84cf-145">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d84cf-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d84cf-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
