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
ms.openlocfilehash: 99eef6b8c264e21df7f4ecf9fc79dc607d484a0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115425"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="69ce1-102">\<ThrowUnobservedTaskExceptions> Element</span><span class="sxs-lookup"><span data-stu-id="69ce1-102">\<ThrowUnobservedTaskExceptions> Element</span></span>
<span data-ttu-id="69ce1-103">指定未處理的工作例外狀況是否應終止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="69ce1-103">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
<span data-ttu-id="69ce1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69ce1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69ce1-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="69ce1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="69ce1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ThrowUnobservedTaskExceptions>**</span><span class="sxs-lookup"><span data-stu-id="69ce1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69ce1-107">語法</span><span class="sxs-lookup"><span data-stu-id="69ce1-107">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69ce1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="69ce1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="69ce1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="69ce1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69ce1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="69ce1-110">Attributes</span></span>  
  
|<span data-ttu-id="69ce1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="69ce1-111">Attribute</span></span>|<span data-ttu-id="69ce1-112">描述</span><span class="sxs-lookup"><span data-stu-id="69ce1-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="69ce1-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="69ce1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="69ce1-114">Specifies whether unhandled task exceptions should terminate the running process.</span><span class="sxs-lookup"><span data-stu-id="69ce1-114">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="69ce1-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="69ce1-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="69ce1-116">值</span><span class="sxs-lookup"><span data-stu-id="69ce1-116">Value</span></span>|<span data-ttu-id="69ce1-117">描述</span><span class="sxs-lookup"><span data-stu-id="69ce1-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="69ce1-118">Does not terminate the running process for an unhandled task exception.</span><span class="sxs-lookup"><span data-stu-id="69ce1-118">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="69ce1-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="69ce1-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="69ce1-120">Terminates the running process for an unhandled task exception.</span><span class="sxs-lookup"><span data-stu-id="69ce1-120">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69ce1-121">子項目</span><span class="sxs-lookup"><span data-stu-id="69ce1-121">Child Elements</span></span>  
 <span data-ttu-id="69ce1-122">無。</span><span class="sxs-lookup"><span data-stu-id="69ce1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69ce1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="69ce1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="69ce1-124">項目</span><span class="sxs-lookup"><span data-stu-id="69ce1-124">Element</span></span>|<span data-ttu-id="69ce1-125">描述</span><span class="sxs-lookup"><span data-stu-id="69ce1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69ce1-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="69ce1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="69ce1-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="69ce1-127">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="69ce1-128">備註</span><span class="sxs-lookup"><span data-stu-id="69ce1-128">Remarks</span></span>  
 <span data-ttu-id="69ce1-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span><span class="sxs-lookup"><span data-stu-id="69ce1-129">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="69ce1-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span><span class="sxs-lookup"><span data-stu-id="69ce1-130">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="69ce1-131">The termination of the process is determined by the timing of garbage collection and finalization.</span><span class="sxs-lookup"><span data-stu-id="69ce1-131">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="69ce1-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span><span class="sxs-lookup"><span data-stu-id="69ce1-132">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="69ce1-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span><span class="sxs-lookup"><span data-stu-id="69ce1-133">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="69ce1-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span><span class="sxs-lookup"><span data-stu-id="69ce1-134">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="69ce1-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span><span class="sxs-lookup"><span data-stu-id="69ce1-135">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="69ce1-136">You can also specify the exception behavior in one of the following ways:</span><span class="sxs-lookup"><span data-stu-id="69ce1-136">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="69ce1-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span><span class="sxs-lookup"><span data-stu-id="69ce1-137">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="69ce1-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span><span class="sxs-lookup"><span data-stu-id="69ce1-138">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69ce1-139">範例</span><span class="sxs-lookup"><span data-stu-id="69ce1-139">Example</span></span>  
 <span data-ttu-id="69ce1-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span><span class="sxs-lookup"><span data-stu-id="69ce1-140">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="69ce1-141">範例</span><span class="sxs-lookup"><span data-stu-id="69ce1-141">Example</span></span>  
 <span data-ttu-id="69ce1-142">The following example demonstrates how an unobserved exception is thrown from a task.</span><span class="sxs-lookup"><span data-stu-id="69ce1-142">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="69ce1-143">The code must be run as a released program to work correctly.</span><span class="sxs-lookup"><span data-stu-id="69ce1-143">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="69ce1-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="69ce1-144">See also</span></span>

- [<span data-ttu-id="69ce1-145">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="69ce1-145">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="69ce1-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="69ce1-146">Configuration File Schema</span></span>](../index.md)
