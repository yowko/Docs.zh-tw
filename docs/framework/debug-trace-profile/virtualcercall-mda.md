---
title: virtualCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f0c06eef7524c18e252ade9122d8c9cb3c2f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="f5a62-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="f5a62-102">virtualCERCall MDA</span></span>
<span data-ttu-id="f5a62-103">`virtualCERCall` Managed 偵錯助理 (MDA) 會以警告模式啟動，指示限制的執行區域 (CER) 呼叫圖形內的呼叫位置會參考虛擬目標，也就是對非 final 虛擬方法的虛擬呼叫或使用介面的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f5a62-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="f5a62-104">通用語言執行平台 (CLR) 無法單從中繼語言和中繼資料分析來預測這些呼叫的目標方法。</span><span class="sxs-lookup"><span data-stu-id="f5a62-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="f5a62-105">因此，無法將呼叫樹狀結構準備為 CER 圖形的一部分，而且無法自動封鎖在該樹狀子目錄內中止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f5a62-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="f5a62-106">這個 MDA 會在下列情況下發出警告：在執行階段已知計算呼叫目標所需的其他資訊時，可能需要使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法的明確呼叫來擴充 CER。</span><span class="sxs-lookup"><span data-stu-id="f5a62-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f5a62-107">徵兆 </span><span class="sxs-lookup"><span data-stu-id="f5a62-107">Symptoms</span></span>  
 <span data-ttu-id="f5a62-108">不會在中止執行緒或卸載應用程式定義域時執行的 CER。</span><span class="sxs-lookup"><span data-stu-id="f5a62-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f5a62-109">原因</span><span class="sxs-lookup"><span data-stu-id="f5a62-109">Cause</span></span>  
 <span data-ttu-id="f5a62-110">CER 包含了對無法自動準備之虛擬方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f5a62-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f5a62-111">解決方式</span><span class="sxs-lookup"><span data-stu-id="f5a62-111">Resolution</span></span>  
 <span data-ttu-id="f5a62-112">為虛擬方法呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>。</span><span class="sxs-lookup"><span data-stu-id="f5a62-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f5a62-113">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="f5a62-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="f5a62-114">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="f5a62-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f5a62-115">輸出</span><span class="sxs-lookup"><span data-stu-id="f5a62-115">Output</span></span>  
  
```  
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f5a62-116">組態</span><span class="sxs-lookup"><span data-stu-id="f5a62-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    < VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f5a62-117">範例</span><span class="sxs-lookup"><span data-stu-id="f5a62-117">Example</span></span>  
  
```  
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of   
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5a62-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a62-118">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f5a62-119">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="f5a62-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f5a62-120">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="f5a62-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
