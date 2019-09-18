---
title: 啟用 JIT 附加偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052830"
---
# <a name="enabling-jit-attach-debugging"></a>啟用 JIT 附加偵錯
JIT 附加偵錯是當您將偵錯工具附加至處理序發生錯誤時，所使用的描述語句，或者可為特定的方法或函式所觸發。  
  
 下列錯誤條件下會使用 JIT 附加偵錯：  
  
- 未處理的例外狀況 (在原生和 Managed 程式碼中)。  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> 方法或 [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) 函式 (Windows 7 系列)。  
  
- 執行階段嚴重錯誤。  
  
 呼叫下列方法和函式也會觸發 JIT 附加偵錯：  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> 方法。  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> 方法。  
  
- [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) 函式 (Win32)。  
  
 在 .NET Framework 4 之前，.NET Framework 提供個別的登錄機碼來控制原生和 managed 偵錯工具的行為。 從 .NET Framework 4 開始，控制權會合並在單一登入機碼底下：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. 您可為該機碼設定的值，會決定是否叫用偵錯工具；而如果決定叫用，是否使用需要使用者互動的對話方塊叫用。 如需設定此登錄機碼的相關資訊，請參閱設定[自動的調試](https://go.microsoft.com/fwlink/?LinkId=181767)程式。  
  
## <a name="see-also"></a>另請參閱

- [偵錯、追蹤和程式碼剖析](index.md)
- [使映像偵錯更容易](making-an-image-easier-to-debug.md)
