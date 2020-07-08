---
title: memberInfoCacheCreation MDA
description: 瞭解 .NET 中的 memberInfoCacheCreation managed 偵錯工具（MDA），這會在建立 MemberInfo 快取時啟動。
ms.date: 03/30/2017
helpviewer_keywords:
- member info cache creation
- MemberInfoCacheCreation MDA
- reflection, run-time errors
- MDAs (managed debugging assistants), cache
- cache [.NET Framework], reflection
- managed debugging assistants (MDAs), cache
- MemberInfo cache
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
ms.openlocfilehash: c48be7ac8632b8072981be01e01997ee8c34b6b3
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051138"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="fa9cb-103">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="fa9cb-103">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="fa9cb-104">建立 <xref:System.Reflection.MemberInfo> 快取時，會啟用 `memberInfoCacheCreation` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-104">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="fa9cb-105">這明顯指出利用耗用大量資源之反映功能的程式。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-105">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fa9cb-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="fa9cb-106">Symptoms</span></span>  
 <span data-ttu-id="fa9cb-107">程式的工作集會增加，因為程式正在使用耗用大量資源的反映。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-107">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fa9cb-108">原因</span><span class="sxs-lookup"><span data-stu-id="fa9cb-108">Cause</span></span>  
 <span data-ttu-id="fa9cb-109">包含 <xref:System.Reflection.MemberInfo> 物件的反映作業會耗用大量資源，因為它們必須讀取冷頁面中所儲存的中繼資料，而且一般會指出程式正在使用某種類型的晚期繫結案例。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-109">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fa9cb-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="fa9cb-110">Resolution</span></span>  
 <span data-ttu-id="fa9cb-111">您可以啟用此 MDA，然後在偵錯工具中執行程式碼，或在啟用 MDA 時使用偵錯工具附加，來判斷將在程式中使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-111">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="fa9cb-112">透過偵錯工具，您將取得堆疊追蹤以顯示 <xref:System.Reflection.MemberInfo> 快取建立位置，並且您可以在該處判斷程式將使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-112">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="fa9cb-113">解決方式取決於程式碼目標。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-113">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="fa9cb-114">此 MDA 會提醒您程式具有晚期繫結案例。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-114">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="fa9cb-115">您可能想要決定是否可以替代早期繫結案例，或考慮晚期繫結案例的效能。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-115">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fa9cb-116">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="fa9cb-116">Effect on the Runtime</span></span>  
 <span data-ttu-id="fa9cb-117">會針對每個建立的 <xref:System.Reflection.MemberInfo> 快取啟用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-117">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="fa9cb-118">效能影響微不足道。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-118">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fa9cb-119">輸出</span><span class="sxs-lookup"><span data-stu-id="fa9cb-119">Output</span></span>  
 <span data-ttu-id="fa9cb-120">MDA 會輸出訊息，指出已建立 <xref:System.Reflection.MemberInfo> 快取。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-120">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="fa9cb-121">使用偵錯工具取得堆疊追蹤，以顯示將在程式中使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-121">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fa9cb-122">組態</span><span class="sxs-lookup"><span data-stu-id="fa9cb-122">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="fa9cb-123">範例</span><span class="sxs-lookup"><span data-stu-id="fa9cb-123">Example</span></span>  
 <span data-ttu-id="fa9cb-124">此範例程式碼將會啟用 `memberInfoCacheCreation` MDA。</span><span class="sxs-lookup"><span data-stu-id="fa9cb-124">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
```csharp
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa9cb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa9cb-125">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="fa9cb-126">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="fa9cb-126">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
