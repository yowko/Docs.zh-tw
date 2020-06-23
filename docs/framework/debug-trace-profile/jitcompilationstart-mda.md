---
title: jitCompilationStart MDA
description: 使用 jitCompilationStart managed 偵錯工具（MDA），此功能會在即時（JIT）編譯器開始編譯 .NET 函式時開始報告。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: bf2d09f433f0b8e4056fecd1f4e82bf3b91dd2bc
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904126"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="3c12f-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="3c12f-103">jitCompilationStart MDA</span></span>
<span data-ttu-id="3c12f-104">當 Just-In-time (JIT) 編譯器開始編譯函式時，會啟動 `jitCompilationStart` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="3c12f-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3c12f-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="3c12f-105">Symptoms</span></span>  
 <span data-ttu-id="3c12f-106">因為 mscorjit.dll 已載入至處理序，所以已經是原生映像格式的程式的工作集大小會增加。</span><span class="sxs-lookup"><span data-stu-id="3c12f-106">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3c12f-107">原因</span><span class="sxs-lookup"><span data-stu-id="3c12f-107">Cause</span></span>  
 <span data-ttu-id="3c12f-108">並非所有與程式相依的組件都是以原生格式產生，或者以原生格式產生的組件未正確登錄。</span><span class="sxs-lookup"><span data-stu-id="3c12f-108">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3c12f-109">解決方案</span><span class="sxs-lookup"><span data-stu-id="3c12f-109">Resolution</span></span>  
 <span data-ttu-id="3c12f-110">啟用此 MDA 可讓您判斷哪一個函式正在進行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="3c12f-110">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="3c12f-111">判斷包含函式的組件是否以原生格式產生，並已正確登錄。</span><span class="sxs-lookup"><span data-stu-id="3c12f-111">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3c12f-112">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="3c12f-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="3c12f-113">此 MDA 會在方法剛要進行 JIT 編譯之前記錄訊息，所以啟用此 MDA 會對效能造成重大影響。</span><span class="sxs-lookup"><span data-stu-id="3c12f-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="3c12f-114">請注意，如果是內嵌的方法，這個 MDA 就不會另行產生訊息。</span><span class="sxs-lookup"><span data-stu-id="3c12f-114">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3c12f-115">輸出</span><span class="sxs-lookup"><span data-stu-id="3c12f-115">Output</span></span>  
 <span data-ttu-id="3c12f-116">下列程式碼範例會顯示範例輸出。</span><span class="sxs-lookup"><span data-stu-id="3c12f-116">The following code sample shows sample output.</span></span> <span data-ttu-id="3c12f-117">在本例中，輸出會顯示在組件 Test 中，類別 "ns2.CO" 上的方法 "m" 已經 JIT 編譯過。</span><span class="sxs-lookup"><span data-stu-id="3c12f-117">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="3c12f-118">設定</span><span class="sxs-lookup"><span data-stu-id="3c12f-118">Configuration</span></span>  
 <span data-ttu-id="3c12f-119">下列組態檔顯示的各種篩選器，可用來篩選出第一次 JIT 編譯時要報告哪些方法。</span><span class="sxs-lookup"><span data-stu-id="3c12f-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="3c12f-120">您可以將 name 屬性的值設定為，以指定報告所有方法 \* 。</span><span class="sxs-lookup"><span data-stu-id="3c12f-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3c12f-121">範例</span><span class="sxs-lookup"><span data-stu-id="3c12f-121">Example</span></span>  
 <span data-ttu-id="3c12f-122">下列程式碼範例是用來搭配先前的組態檔。</span><span class="sxs-lookup"><span data-stu-id="3c12f-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c12f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c12f-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3c12f-124">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="3c12f-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3c12f-125">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="3c12f-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
