---
title: pInvokeStackImbalance MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9938db3f4a3d054fde52139c166fb6a2e2a402df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="pinvokestackimbalance-mda"></a>pInvokeStackImbalance MDA
假設 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性中已指定呼叫慣例並已宣告Managed 簽章中的參數，當 CLR 在平台叫用呼叫之後偵測到有堆疊深度不符合預期的堆疊深度時，便會啟動 `pInvokeStackImbalance` Managed 偵錯助理 (MDA)。  
  
> [!NOTE]
>  `pInvokeStackImbalance` MDA 只會在 32 位元 x86 平台上實作。  
  
> [!NOTE]
>  在 .NET Framework 3.5 版中，預設會停用 `pInvokeStackImbalance` MDA。 當您搭配使用 .NET Framework 3.5 版與 Visual Studio 2005 時，`pInvokeStackImbalance` MDA 會出現在 [例外狀況] 對話方塊的 [Managed 偵錯助理] 清單中 (當您按一下 [偵錯] 功能表上的 [例外狀況] 時會顯示 [例外狀況] 對話方塊)。 不過，選取或清除 `pInvokeStackImbalance` 的 [擲回] 核取方塊並不會啟用或停用 MDA，而只會控制 Visual Studio 是否在啟動 MDA 時擲回例外狀況。  
  
## <a name="symptoms"></a>徵兆  
 應用程式在進行平台叫用呼叫期間或之後發生存取違規或記憶體損毀。  
  
## <a name="cause"></a>原因  
 平台叫用呼叫的 Managed 簽章可能與所呼叫之方法的 Unmanaged 簽章不符。  當 Managed 簽章未宣告正確的參數數目，或未指定適當的參數大小時，便會造成這種不相符狀況。  MDA 也可能由於呼叫慣例 (可能由 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性指定) 與 Unmanaged 呼叫慣例不符而啟動。  
  
## <a name="resolution"></a>解決方式  
 檢閱 Managed 平台叫用簽章和呼叫慣例，確認其與原生目標的簽章和呼叫慣例相符。  嘗試明確指定 Managed 和 Unmanaged 端的呼叫慣例。 Unmanaged 函式也可能 (雖然可能性不高) 因其他一些原因而使堆疊失去平衡，例如 Unmanaged 編譯器中的 Bug。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 強制所有平台叫用呼叫採用 CLR 中未最佳化的路徑。  
  
## <a name="output"></a>輸出  
 MDA 訊息會提供使堆疊失去平衡之平台叫用方法呼叫的名稱。  `SampleMethod` 方法之平台叫用呼叫的範例訊息為：  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
