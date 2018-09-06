---
title: 啟用 JIT 附加偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b92592500f0babf29891710cedf1228b0ddcb0e4
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739125"
---
# <a name="enabling-jit-attach-debugging"></a>啟用 JIT 附加偵錯
JIT 附加偵錯是當您將偵錯工具附加至處理序發生錯誤時，所使用的描述語句，或者可為特定的方法或函式所觸發。  
  
 下列錯誤條件下會使用 JIT 附加偵錯：  
  
-   未處理的例外狀況 (在原生和 Managed 程式碼中)。  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) 函式 (Windows 7 系列)。  
  
-   執行階段嚴重錯誤。  
  
 呼叫下列方法和函式也會觸發 JIT 附加偵錯：  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。  
  
-   [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) 函式 (Win32)。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 之前，.NET Framework 會提供不同的登錄機碼控制原生和 Managed 偵錯工具的行為。 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，控制會彙總在單一登錄機碼下：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug。 您可為該機碼設定的值，會決定是否叫用偵錯工具；而如果決定叫用，是否使用需要使用者互動的對話方塊叫用。 如需設定此登錄機碼的資訊，請參閱[設定自動偵錯](https://go.microsoft.com/fwlink/?LinkId=181767)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯、追蹤和程式碼剖析](../../../docs/framework/debug-trace-profile/index.md)  
 [使映像偵錯更容易](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [啟用分析](https://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
