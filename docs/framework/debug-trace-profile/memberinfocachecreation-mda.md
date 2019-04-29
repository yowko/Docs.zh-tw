---
title: memberInfoCacheCreation MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90f59f4d593a8aa077a6710cc0f5c1747ac1a3ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753995"
---
# <a name="memberinfocachecreation-mda"></a><span data-ttu-id="fd0c2-102">memberInfoCacheCreation MDA</span><span class="sxs-lookup"><span data-stu-id="fd0c2-102">memberInfoCacheCreation MDA</span></span>
<span data-ttu-id="fd0c2-103">建立 <xref:System.Reflection.MemberInfo> 快取時，會啟用 `memberInfoCacheCreation` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-103">The `memberInfoCacheCreation` managed debugging assistant (MDA) is activated when a <xref:System.Reflection.MemberInfo> cache is created.</span></span> <span data-ttu-id="fd0c2-104">這明顯指出利用耗用大量資源之反映功能的程式。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-104">This is a strong indication of a program that is making use of resource-expensive reflection features.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fd0c2-105">徵兆</span><span class="sxs-lookup"><span data-stu-id="fd0c2-105">Symptoms</span></span>  
 <span data-ttu-id="fd0c2-106">程式的工作集會增加，因為程式正在使用耗用大量資源的反映。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-106">A program's working set increases because the program is using resource-expensive reflection.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fd0c2-107">原因</span><span class="sxs-lookup"><span data-stu-id="fd0c2-107">Cause</span></span>  
 <span data-ttu-id="fd0c2-108">包含 <xref:System.Reflection.MemberInfo> 物件的反映作業會耗用大量資源，因為它們必須讀取冷頁面中所儲存的中繼資料，而且一般會指出程式正在使用某種類型的晚期繫結案例。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-108">Reflection operations that involve <xref:System.Reflection.MemberInfo> objects are considered resource expensive because they must read metadata that is stored in cold pages and in general they indicate the program is using some type of late-bound scenario.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fd0c2-109">解決方式</span><span class="sxs-lookup"><span data-stu-id="fd0c2-109">Resolution</span></span>  
 <span data-ttu-id="fd0c2-110">您可以啟用此 MDA，然後在偵錯工具中執行程式碼，或在啟用 MDA 時使用偵錯工具附加，來判斷將在程式中使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-110">You can determine where reflection is being used in your program by enabling this MDA and then running your code in a debugger or attaching with a debugger when the MDA is activated.</span></span> <span data-ttu-id="fd0c2-111">透過偵錯工具，您將取得堆疊追蹤以顯示 <xref:System.Reflection.MemberInfo> 快取建立位置，並且您可以在該處判斷程式將使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-111">Under a debugger you will get a stack trace showing where the <xref:System.Reflection.MemberInfo> cache was created and from there you can determine where your program is using reflection.</span></span>  
  
 <span data-ttu-id="fd0c2-112">解決方式取決於程式碼目標。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-112">The resolution is dependent on the objectives of the code.</span></span> <span data-ttu-id="fd0c2-113">此 MDA 會提醒您程式具有晚期繫結案例。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-113">This MDA alerts you that your program has a late-bound scenario.</span></span> <span data-ttu-id="fd0c2-114">您可能想要決定是否可以替代早期繫結案例，或考慮晚期繫結案例的效能。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-114">You might want to determine if you can substitute an early-bound scenario or consider the performance of the late bound scenario.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fd0c2-115">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="fd0c2-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="fd0c2-116">會針對每個建立的 <xref:System.Reflection.MemberInfo> 快取啟用此 MDA。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-116">This MDA is activated for every <xref:System.Reflection.MemberInfo> cache that is created.</span></span> <span data-ttu-id="fd0c2-117">效能影響微不足道。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-117">The performance impact is negligible.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fd0c2-118">Output</span><span class="sxs-lookup"><span data-stu-id="fd0c2-118">Output</span></span>  
 <span data-ttu-id="fd0c2-119">MDA 會輸出訊息，指出已建立 <xref:System.Reflection.MemberInfo> 快取。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-119">The MDA outputs a message indicating the <xref:System.Reflection.MemberInfo> cache was created.</span></span> <span data-ttu-id="fd0c2-120">使用偵錯工具取得堆疊追蹤，以顯示將在程式中使用反映的位置。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-120">Use a debugger to get a stack trace showing where your program is using reflection.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fd0c2-121">組態</span><span class="sxs-lookup"><span data-stu-id="fd0c2-121">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="fd0c2-122">範例</span><span class="sxs-lookup"><span data-stu-id="fd0c2-122">Example</span></span>  
 <span data-ttu-id="fd0c2-123">此範例程式碼將會啟用 `memberInfoCacheCreation` MDA。</span><span class="sxs-lookup"><span data-stu-id="fd0c2-123">This sample code will activate the `memberInfoCacheCreation` MDA.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd0c2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd0c2-124">See also</span></span>

- <xref:System.Reflection.MemberInfo>
- [<span data-ttu-id="fd0c2-125">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="fd0c2-125">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
