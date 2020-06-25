---
title: jitCompilationStart managed 偵錯工具（MDA）
description: 當即時（JIT）編譯器開始編譯 .NET 函式時，會報告 jitCompilationStart managed 偵錯工具（MDA）。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325534"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="96e90-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="96e90-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="96e90-104">當 Just-In-time (JIT) 編譯器開始編譯函式時，會啟動 `jitCompilationStart` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="96e90-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="96e90-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="96e90-105">Symptoms</span></span>  
 <span data-ttu-id="96e90-106">已是原生影像格式之程式的工作集大小會增加，因為 mscorjit.dll 會載入至進程中。</span><span class="sxs-lookup"><span data-stu-id="96e90-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="96e90-107">原因</span><span class="sxs-lookup"><span data-stu-id="96e90-107">Cause</span></span>  
<span data-ttu-id="96e90-108">並非程式相依的所有元件都是以原生格式產生，或元件未正確註冊。</span><span class="sxs-lookup"><span data-stu-id="96e90-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="96e90-109">解決方案</span><span class="sxs-lookup"><span data-stu-id="96e90-109">Resolution</span></span>  
 <span data-ttu-id="96e90-110">啟用此 MDA 可讓您識別正在進行 JIT 編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="96e90-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="96e90-111">請確定包含函式的元件會產生原生格式，並已正確註冊。</span><span class="sxs-lookup"><span data-stu-id="96e90-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="96e90-112">對執行時間的影響</span><span class="sxs-lookup"><span data-stu-id="96e90-112">Effect on the runtime</span></span>  
 <span data-ttu-id="96e90-113">此 MDA 會在方法剛要進行 JIT 編譯之前記錄訊息，所以啟用此 MDA 會對效能造成重大影響。</span><span class="sxs-lookup"><span data-stu-id="96e90-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="96e90-114">如果方法是內嵌的，此 MDA 將不會產生個別的訊息。</span><span class="sxs-lookup"><span data-stu-id="96e90-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="96e90-115">輸出</span><span class="sxs-lookup"><span data-stu-id="96e90-115">Output</span></span>  
 <span data-ttu-id="96e90-116">下列程式碼範例會顯示範例輸出。</span><span class="sxs-lookup"><span data-stu-id="96e90-116">The following code sample shows sample output.</span></span> <span data-ttu-id="96e90-117">在此情況下，輸出顯示在元件測試中，類別 "ns2.CO" 上的方法 "m" 已進行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="96e90-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="96e90-118">設定</span><span class="sxs-lookup"><span data-stu-id="96e90-118">Configuration</span></span>  
 <span data-ttu-id="96e90-119">下列組態檔顯示的各種篩選器，可用來篩選出第一次 JIT 編譯時要報告哪些方法。</span><span class="sxs-lookup"><span data-stu-id="96e90-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="96e90-120">您可以將 name 屬性的值設定為，以指定報告所有方法 \* 。</span><span class="sxs-lookup"><span data-stu-id="96e90-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="96e90-121">範例</span><span class="sxs-lookup"><span data-stu-id="96e90-121">Example</span></span>  
 <span data-ttu-id="96e90-122">下列程式碼範例是用來搭配先前的組態檔。</span><span class="sxs-lookup"><span data-stu-id="96e90-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="96e90-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96e90-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="96e90-124">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="96e90-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="96e90-125">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="96e90-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
