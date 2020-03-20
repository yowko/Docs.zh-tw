---
title: virtualCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181715"
---
# <a name="virtualcercall-mda"></a>virtualCERCall MDA
`virtualCERCall` Managed 偵錯助理 (MDA) 會以警告模式啟動，指示限制的執行區域 (CER) 呼叫圖形內的呼叫位置會參考虛擬目標，也就是對非 final 虛擬方法的虛擬呼叫或使用介面的呼叫。 通用語言執行平台 (CLR) 無法單從中繼語言和中繼資料分析來預測這些呼叫的目標方法。 因此，無法將呼叫樹狀結構準備為 CER 圖形的一部分，而且無法自動封鎖在該樹狀子目錄內中止的執行緒。 這個 MDA 會在下列情況下發出警告：在執行階段已知計算呼叫目標所需的其他資訊時，可能需要使用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> 方法的明確呼叫來擴充 CER。  
  
## <a name="symptoms"></a>徵狀  
 不會在中止執行緒或卸載應用程式定義域時執行的 CER。  
  
## <a name="cause"></a>原因  
 CER 包含了對無法自動準備之虛擬方法的呼叫。  
  
## <a name="resolution"></a>解決方案  
 為虛擬方法呼叫 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  
  
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
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [使用 Managed 偵錯助理診斷錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
