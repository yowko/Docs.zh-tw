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
ms.openlocfilehash: 9ecdfd708217f260b0c02383159fab88948029c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512312"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance MDA

`PInvokeStackImbalance` Managed 偵錯助理 (MDA) 會啟動，當 CLR 偵測到的平台叫用呼叫之後的堆疊深度不符合預期的堆疊深度，指定在指定的呼叫慣例<xref:System.Runtime.InteropServices.DllImportAttribute>屬性，宣告 managed 簽章中的參數。

`PInvokeStackImbalance` MDA 只會在 32 位元 x86 平台上實作。

> [!NOTE]
> `PInvokeStackImbalance`預設會停用 MDA。 在 Visual Studio 2017 中， `PInvokeStackImbalance` MDA 會出現在**Managed 偵錯助理**清單中**例外狀況設定**對話方塊中 (這會顯示當您選取**偵錯** >  **Windows** > **例外狀況設定**)。 不過，選取或清除**中斷時擲回**核取方塊不會啟用或停用 MDA，而只會控制在啟動 MDA 時，Visual Studio 是否會發生例外狀況。

## <a name="symptoms"></a>徵兆

應用程式在進行平台叫用呼叫期間或之後發生存取違規或記憶體損毀。

## <a name="cause"></a>原因

平台叫用呼叫的 Managed 簽章可能與所呼叫之方法的 Unmanaged 簽章不符。  當 Managed 簽章未宣告正確的參數數目，或未指定適當的參數大小時，便會造成這種不相符狀況。  MDA 也可能由於呼叫慣例 (可能由 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性指定) 與 Unmanaged 呼叫慣例不符而啟動。

## <a name="resolution"></a>解決方式

檢閱 Managed 平台叫用簽章和呼叫慣例，確認其與原生目標的簽章和呼叫慣例相符。  嘗試明確指定 Managed 和 Unmanaged 端的呼叫慣例。 Unmanaged 函式也可能 (雖然可能性不高) 因其他一些原因而使堆疊失去平衡，例如 Unmanaged 編譯器中的 Bug。

## <a name="effect-on-the-runtime"></a>對執行階段的影響

強制所有平台叫用呼叫採用 CLR 中未最佳化的路徑。

## <a name="output"></a>輸出

MDA 訊息會提供使堆疊失去平衡之平台叫用方法呼叫的名稱。 `SampleMethod` 方法之平台叫用呼叫的範例訊息為：

**呼叫 PInvoke 函式 'SampleMethod' 有不對稱的堆疊。這可能是因為 managed 的 PInvoke 簽章與未受管理的目標簽章不相符。請檢查的呼叫慣例和 PInvoke 簽章的參數相符的目標 unmanaged 簽章。**

## <a name="configuration"></a>組態

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
