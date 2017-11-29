---
title: jitCompilationStart MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 67c80fce223d8f212fa485a8105862bcf24e161b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="2ae3e-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="2ae3e-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="2ae3e-103">當 Just-In-time (JIT) 編譯器開始編譯函式時，會啟動 `jitCompilationStart` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2ae3e-104">徵兆 </span><span class="sxs-lookup"><span data-stu-id="2ae3e-104">Symptoms</span></span>  
 <span data-ttu-id="2ae3e-105">因為 mscorjit.dll 已載入至處理序，所以已經是原生映像格式的程式的工作集大小會增加。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2ae3e-106">原因</span><span class="sxs-lookup"><span data-stu-id="2ae3e-106">Cause</span></span>  
 <span data-ttu-id="2ae3e-107">並非所有與程式相依的組件都是以原生格式產生，或者以原生格式產生的組件未正確登錄。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2ae3e-108">解決方式</span><span class="sxs-lookup"><span data-stu-id="2ae3e-108">Resolution</span></span>  
 <span data-ttu-id="2ae3e-109">啟用此 MDA 可讓您判斷哪一個函式正在進行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="2ae3e-110">判斷包含函式的組件是否以原生格式產生，並已正確登錄。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2ae3e-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="2ae3e-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="2ae3e-112">此 MDA 會在方法剛要進行 JIT 編譯之前記錄訊息，所以啟用此 MDA 會對效能造成重大影響。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="2ae3e-113">請注意，如果是內嵌的方法，這個 MDA 就不會另行產生訊息。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2ae3e-114">輸出</span><span class="sxs-lookup"><span data-stu-id="2ae3e-114">Output</span></span>  
 <span data-ttu-id="2ae3e-115">下列程式碼範例會顯示範例輸出。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-115">The following code sample shows sample output.</span></span> <span data-ttu-id="2ae3e-116">在本例中，輸出會顯示在組件 Test 中，類別 "ns2.CO" 上的方法 "m" 已經 JIT 編譯過。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="2ae3e-117">組態</span><span class="sxs-lookup"><span data-stu-id="2ae3e-117">Configuration</span></span>  
 <span data-ttu-id="2ae3e-118">下列組態檔顯示的各種篩選器，可用來篩選出第一次 JIT 編譯時要報告哪些方法。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="2ae3e-119">您可以將名稱屬性的值設定為 *，指定回報所有的方法。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-119">You can specify that all methods be reported by setting the value of the name attribute to *.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2ae3e-120">範例</span><span class="sxs-lookup"><span data-stu-id="2ae3e-120">Example</span></span>  
 <span data-ttu-id="2ae3e-121">下列程式碼範例是用來搭配先前的組態檔。</span><span class="sxs-lookup"><span data-stu-id="2ae3e-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ae3e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ae3e-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="2ae3e-123">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="2ae3e-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="2ae3e-124">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="2ae3e-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
