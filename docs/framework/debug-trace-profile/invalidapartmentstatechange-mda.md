---
title: invalidApartmentStateChange MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid apartment state
- managed debugging assistants (MDAs), invalid apartment state
- InvalidApartmentStateChange MDA
- invalid apartment state changes
- threading [.NET Framework], apartment states
- apartment states
- threading [.NET Framework], managed debugging assistants
- COM apartment states
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73f96ea8cf215c1392857635e85556f530784397
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147648"
---
# <a name="invalidapartmentstatechange-mda"></a>invalidApartmentStateChange MDA
`invalidApartmentStateChange` Managed 偵錯助理 (MDA) 是由下列兩個問題之一所啟動：  
  
-   嘗試變更執行緒的 COM Apartment 狀態，該執行緒已被 COM 初始化成不同的 Apartment 狀態。  
  
-   未預期的執行緒 COM Apartment 狀態變更。  
  
## <a name="symptoms"></a>徵兆  
  
-   執行緒的 COM Apartment 狀態不是原來要求的。 這可能會導致 Proxy 用於執行緒模型和目前執行緒模型不同的 COM 元件。 接著，在透過未設定跨 Apartment 封送處理的介面呼叫 COM 物件時，這可能會造成 <xref:System.InvalidCastException> 被擲回。  
  
-   執行緒的 COM Apartment 狀態與預期的不同。 在[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) 上進行呼叫時，這會造成 <xref:System.Runtime.InteropServices.COMException> 具有 RPC_E_WRONG_THREAD 的 HRESULT 以及 <xref:System.InvalidCastException>。 這也會造成多個執行緒同時存取某些單一執行緒的 COM 元件，導致損毀或資料遺失。  
  
## <a name="cause"></a>原因  
  
-   執行緒先前已初始化成不同的 COM Apartment 狀態。 請注意，可以明確或隱含方式設定執行緒的 Apartment 狀態。 明確的作業包括 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=nameWithType> 屬性以及 <xref:System.Threading.Thread.SetApartmentState%2A> 和 <xref:System.Threading.Thread.TrySetApartmentState%2A> 方法。 使用 <xref:System.Threading.Thread.Start%2A> 方法建立的執行緒，會以隱含方式設成 <xref:System.Threading.ApartmentState.MTA>，除非啟動執行緒之前呼叫 <xref:System.Threading.Thread.SetApartmentState%2A>。 應用程式的主執行緒也會以隱含方式初始化為 <xref:System.Threading.ApartmentState.MTA>，除非在 Main 方法上指定 <xref:System.STAThreadAttribute> 屬性。  
  
-   在執行緒上呼叫具有不同並行模型的 `CoUninitialize` 方法 (或 `CoInitializeEx` 方法)。  
  
## <a name="resolution"></a>解決方式  
 請先設定執行緒的 Apartment 狀態再開始執行，或將 <xref:System.STAThreadAttribute> 屬性或 <xref:System.MTAThreadAttribute> 屬性套用到應用程式的 Main 方法。  
  
 第二個原因，在理想情況下，應該修改呼叫 `CoUninitialize` 方法的程式碼以延遲呼叫，直到執行緒即將終止且沒有任何 RCW 為止，執行緒仍繼續使用它們的基礎 COM 元件。 不過，如果不可能修改呼叫 `CoUninitialize` 方法的程式碼，則不應從未以此方式初始化的執行緒中使用任何 RCW。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  
 目前執行緒的 COM Apartment 狀態和程式碼之前嘗試套用的狀態。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範可以啟動此 MDA 的情況。  
  
```csharp
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
