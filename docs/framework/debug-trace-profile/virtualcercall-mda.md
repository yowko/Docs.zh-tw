---
title: virtualCERCall MDA
description: 檢查 virtualCERCall managed 偵錯工具 (MDA) ，如果 CER 包含無法自動準備的虛擬方法呼叫，則會叫用此功能。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: c3e8060702239c6f87659f48658160e46491542f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257089"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="0aec6-103">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="0aec6-103">virtualCERCall MDA</span></span>

<span data-ttu-id="0aec6-104">`virtualCERCall` Managed 偵錯助理 (MDA) 會以警告模式啟動，指示限制的執行區域 (CER) 呼叫圖形內的呼叫位置會參考虛擬目標，也就是對非 final 虛擬方法的虛擬呼叫或使用介面的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0aec6-104">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="0aec6-105">通用語言執行平台 (CLR) 無法單從中繼語言和中繼資料分析來預測這些呼叫的目標方法。</span><span class="sxs-lookup"><span data-stu-id="0aec6-105">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="0aec6-106">因此，無法將呼叫樹狀結構準備為 CER 圖形的一部分，而且無法自動封鎖在該樹狀子目錄內中止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="0aec6-106">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="0aec6-107">這個 MDA 會在下列情況下發出警告：在執行階段已知計算呼叫目標所需的其他資訊時，可能需要使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法的明確呼叫來擴充 CER。</span><span class="sxs-lookup"><span data-stu-id="0aec6-107">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0aec6-108">徵狀</span><span class="sxs-lookup"><span data-stu-id="0aec6-108">Symptoms</span></span>  

 <span data-ttu-id="0aec6-109">不會在中止執行緒或卸載應用程式定義域時執行的 CER。</span><span class="sxs-lookup"><span data-stu-id="0aec6-109">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0aec6-110">原因</span><span class="sxs-lookup"><span data-stu-id="0aec6-110">Cause</span></span>  

 <span data-ttu-id="0aec6-111">CER 包含了對無法自動準備之虛擬方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0aec6-111">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0aec6-112">解決方法</span><span class="sxs-lookup"><span data-stu-id="0aec6-112">Resolution</span></span>  

 <span data-ttu-id="0aec6-113">為虛擬方法呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>。</span><span class="sxs-lookup"><span data-stu-id="0aec6-113">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0aec6-114">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0aec6-114">Effect on the Runtime</span></span>  

 <span data-ttu-id="0aec6-115">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0aec6-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0aec6-116">輸出</span><span class="sxs-lookup"><span data-stu-id="0aec6-116">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="0aec6-117">設定</span><span class="sxs-lookup"><span data-stu-id="0aec6-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0aec6-118">範例</span><span class="sxs-lookup"><span data-stu-id="0aec6-118">Example</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="0aec6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aec6-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0aec6-120">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0aec6-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0aec6-121">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0aec6-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
