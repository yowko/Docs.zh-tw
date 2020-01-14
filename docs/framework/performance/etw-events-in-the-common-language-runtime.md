---
title: Common Language Runtime 中的 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: 49d1141540fb00ab7ef462da5af84f02e6d9fc4d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937862"
---
# <a name="etw-events-in-the-common-language-runtime"></a>Common Language Runtime 中的 ETW 事件
Common language runtime (CLR) 透過各式各樣的偵錯和分析事件，提供有用的 Windows 事件追蹤 (ETW) 診斷資訊。 CLR ETW 事件會運用 Windows ETW 追蹤系統，來增強 Common Language Runtime 提供的現有分析和偵錯支援。  
  
 如需 ETW 的詳細資訊，請參閱[使用 Etw 改善調試和效能微調](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)一文。 您可以在 NTDebugging 部落格的 [Windows 效能工具組 - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) 一文中找到 Xperf 的相關資訊。  
  
 事件主題中所述的所有事件都需要 .NET Framework 4 或更新版本。 Windows Vista 作業系統是支援的最低需求用戶端，而 Windows Server 2008 是支援的最低需求伺服器。  
  
## <a name="in-this-section"></a>本章節內容  
 [控制 .NET Framework 記錄](controlling-logging.md)  
 描述擷取及檢視 ETW 事件的工具與命令。  
  
 [CLR ETW 提供者](clr-etw-providers.md)  
 提供執行階段和取消提供者的相關資訊，以及您如何使用它們處理 ETW 資料收集。  
  
 [CLR ETW 關鍵字和層級](clr-etw-keywords-and-levels.md)  
 說明可依分類啟用事件篩選的執行階段和取消提供者的關鍵字。  
  
 [CLR ETW 事件](clr-etw-events.md)  
 提供 CLR ETW 事件、其關鍵字、層級和事件資料的詳細資訊。  
  
## <a name="see-also"></a>請參閱

- [.NET Framework 中的 ETW 事件](etw-events.md)
