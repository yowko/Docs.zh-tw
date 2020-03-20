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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153811"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="3b0b9-102">\<引發未觀察到的任務異常>元素</span><span class="sxs-lookup"><span data-stu-id="3b0b9-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="3b0b9-103">指定未處理的工作例外狀況是否應終止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="3b0b9-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b0b9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b0b9-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3b0b9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3b0b9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<引發未觀察到的任務異常>**</span><span class="sxs-lookup"><span data-stu-id="3b0b9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b0b9-107">語法</span><span class="sxs-lookup"><span data-stu-id="3b0b9-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b0b9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3b0b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b0b9-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b0b9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3b0b9-110">Attributes</span></span>  
  
|<span data-ttu-id="3b0b9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3b0b9-111">Attribute</span></span>|<span data-ttu-id="3b0b9-112">描述</span><span class="sxs-lookup"><span data-stu-id="3b0b9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3b0b9-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b0b9-114">指定未處理的任務異常是否應終止正在運行的進程。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3b0b9-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="3b0b9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3b0b9-116">值</span><span class="sxs-lookup"><span data-stu-id="3b0b9-116">Value</span></span>|<span data-ttu-id="3b0b9-117">描述</span><span class="sxs-lookup"><span data-stu-id="3b0b9-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3b0b9-118">不終止未處理的任務異常的運行進程。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="3b0b9-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3b0b9-120">終止未處理的任務異常的運行進程。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b0b9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3b0b9-121">Child Elements</span></span>  
 <span data-ttu-id="3b0b9-122">無。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b0b9-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3b0b9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b0b9-124">元素</span><span class="sxs-lookup"><span data-stu-id="3b0b9-124">Element</span></span>|<span data-ttu-id="3b0b9-125">描述</span><span class="sxs-lookup"><span data-stu-id="3b0b9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b0b9-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3b0b9-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="3b0b9-128">備註</span><span class="sxs-lookup"><span data-stu-id="3b0b9-128">Remarks</span></span>  
 <span data-ttu-id="3b0b9-129">如果未觀察到與<xref:System.Threading.Tasks.Task>關聯的異常，則沒有<xref:System.Threading.Tasks.Task.Wait%2A>操作，父項未連接，並且<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>未讀取該屬性，則任務異常被視為未觀察到。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="3b0b9-130">預設情況下，在 .NET 框架 4 中<xref:System.Threading.Tasks.Task>，如果正在回收具有未觀察到異常的 異常，則終端子將引發異常並終止進程。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="3b0b9-131">流程的終止取決於垃圾回收和定稿的時間。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="3b0b9-132">為了使開發人員更容易基於任務編寫非同步代碼，.NET Framework 4.5 會更改此預設行為，以進行未觀察到的異常。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="3b0b9-133">未觀察到的異常仍會導致<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>引發事件，但預設情況下，進程不會終止。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="3b0b9-134">相反，無論事件處理常式是否遵守異常，在引發事件後將忽略異常。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="3b0b9-135">在 .NET 框架 4.5 中，可以使用應用程式佈建檔中的[\<ThrowUnununununtaskexception> 元素](throwunobservedtaskexceptions-element.md)來啟用引發異常的 .NET 框架 4 行為。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="3b0b9-136">還可以通過以下方式之一指定異常行為：</span><span class="sxs-lookup"><span data-stu-id="3b0b9-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="3b0b9-137">通過設置環境變數`COMPlus_ThrowUnobservedTaskExceptions`（。`set COMPlus_ThrowUnobservedTaskExceptions=1`</span><span class="sxs-lookup"><span data-stu-id="3b0b9-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="3b0b9-138">通過設置註冊表 DWORD 值"ThrowUnunun_TaskExceptions " HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft\\中為 1。NETFramework 金鑰。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b0b9-139">範例</span><span class="sxs-lookup"><span data-stu-id="3b0b9-139">Example</span></span>  
 <span data-ttu-id="3b0b9-140">下面的示例演示如何通過使用應用程式佈建檔在任務中啟用異常的引發。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="3b0b9-141">範例</span><span class="sxs-lookup"><span data-stu-id="3b0b9-141">Example</span></span>  
 <span data-ttu-id="3b0b9-142">下面的示例演示如何從任務中引發未觀察到的異常。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="3b0b9-143">代碼必須作為已發佈的程式運行才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="3b0b9-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3b0b9-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b0b9-144">See also</span></span>

- [<span data-ttu-id="3b0b9-145">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3b0b9-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3b0b9-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3b0b9-146">Configuration File Schema</span></span>](../index.md)
