---
title: loaderLock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a70b8c3509b785d70b041b449c759e7994e5984
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754228"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock` Managed 偵錯助理 (MDA) 偵測到在保留 Microsoft Windows 作業系統載入器鎖定的執行緒上，有執行 Managed 程式碼的嘗試。  所有這樣的執行都不合法，因為它可能會產生死結，並在作業系統載入器尚未初始化 DLL 之前就先使用 DLL。  
  
## <a name="symptoms"></a>徵兆  
 在作業系統的載入器鎖定內執行程式碼最常見的失敗，是嘗試呼叫也需要載入器鎖定的其他 Win32 函式時，執行緒會鎖死。  這類函式範例包括 `LoadLibrary`、`GetProcAddress`、`FreeLibrary` 和 `GetModuleHandle`。  應用程式可能不會直接呼叫這些函式。像 <xref:System.Reflection.Assembly.Load%2A> 或平台叫用方法的第一個呼叫等較高層級的呼叫結果，可能是 Common Language Runtime (CLR) 呼叫這些函式。  
  
 當執行緒等候另一個執行緒開始或結束時，也會發生鎖死的情況。  當執行緒開始或結束執行時，它必須取得作業系統的載入器鎖定，以將事件傳遞給受影響的 DLL。  
  
 最後，就會發生作業系統載入器還未正確初始化 DLL 就先呼叫它們的情況。  不同於透過檢查所有與死結有關的執行緒堆疊可診斷出的死結失敗，不使用這個 MDA，要診斷出使用了未初始化的 DLL 很困難。  
  
## <a name="cause"></a>原因  
 針對 .NET Framework 1.0 或 1.1 版建置的混合 Managed/Unmanaged C++ 組件，通常會在載入器鎖定內嘗試執行 Managed 程式碼，除非已特別注意；例如，與 **/NOENTRY** 連結。
  
 針對 .NET Framework 2.0 版建置的混合 Managed/Unmanaged C++ 組件，較不容易發生這些問題，與使用 Unmanaged DLL 違反作業系統規則的應用程式，有相同的降低風險。  例如，如果 Unmanaged DLL 的 `DllMain` 進入點，呼叫 `CoCreateInstance` 取得已向 COM 公開的 Managed 物件，結果是在載入器鎖定內嘗試執行 Managed 程式碼。 如需 .NET Framework 2.0 版或更新版本中的載入器鎖定問題的詳細資訊，請參閱[初始化混合組件](/cpp/dotnet/initialization-of-mixed-assemblies)。  
  
## <a name="resolution"></a>解決方式  
 在 Visual C++ .NET 2002 和 Visual C++ .NET 2003 中，使用 `/clr` 編譯器選項編譯的 DLL，可能會在載入時出現不具決定性的死結；此問題稱為混合 DLL 載入或載入器鎖定問題。 在 Visual C++ 2005 及更新版本中，混合 DLL 載入程序的所有不具決定性問題幾乎都已獲得解決。 不過還是有些情況可能會發生載入器鎖定問題 (具決定性)。 如需其餘載入器鎖定問題的原因與解決方法的詳細說明，請參閱[初始化混合組件](/cpp/dotnet/initialization-of-mixed-assemblies)。 如果在該主題中找不出您的載入器鎖定問題，您必須檢查執行緒的堆疊，以判斷載入器鎖定發生的原因，以及如何修正此問題。 查看已啟動此 MDA 的執行緒堆疊追蹤。  在保留作業系統載入器鎖定時，執行緒嘗試以非法方式呼叫 Managed 程式碼。  您可能會在堆疊上看到 DLL 的 `DllMain` 或對等進入點。  可從這類進入點內部執行哪些合法作業的作業系統規則相當有限。  這些規則會排除所有 Managed 執行。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 一般而言，處理序內有數個執行緒會鎖死。  其中一個執行緒很可能負責執行記憶體回收，因此這個死結對整個程序有很大的影響。  此外，它會防止需要作業系統載入器鎖定的任何其他作業，例如載入及卸載組件或 DLL，以及啟動或停止執行緒。  
  
 在某些罕見的情況下，也可能會在未初始化即被呼叫的 DLL 中，觸發存取違規或類似問題。  
  
## <a name="output"></a>Output  
 此 MDA 會報告正在嘗試不合法的 Managed 執行。  您需要檢查執行緒的堆疊，以判斷載入器鎖定發生的原因，以及如何修正此問題。  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
