---
title: Silverlight 偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790317"
---
# <a name="silverlight-debugging"></a>Silverlight 偵錯
本節中的主題說明 Common Language Runtime (CLR) 為了支援對 Windows 作業系統或 Macintosh 平台上執行的 Silverlight 應用程式進行偵錯，所提供的環境和介面。  
  
## <a name="in-this-section"></a>本章節內容  
 [EnumerateCLRs 函式](enumerateclrs-function.md)  
 提供在處理程序中列舉 CLRs 的機制。  
  
 [CloseCLREnumeration 函式](closeclrenumeration-function.md)  
 關閉位於[EnumerateCLRs](enumerateclrs-function.md)函式所傳回之控制碼陣列中的任何有效 CLR 繼續-啟動事件，並釋放控制碼和字串路徑陣列的記憶體。  
  
 [CreateCoreClrDebugTarget 函式](createcoreclrdebugtarget-function.md)  
 針對處理序和執行階段列舉，建立與遠端目標的連接。  
  
 [CreateCordbObject 函式](createcordbobject-function.md)  
 建立偵錯工具介面，以提供在遠端處理序上具現化 Managed 偵錯工作階段的功能。  
  
 [CreateVersionStringFromModule 函式](createversionstringfrommodule-function.md)  
 從目標處理序中的 CLR 路徑來建立版本字串。  
  
 [CreateDebuggingInterfaceFromVersion 函式](createdebugginginterfacefromversion-function-for-silverlight.md)  
 接受從[CreateVersionStringFromModule](createversionstringfrommodule-function.md)函式函式傳回的 CLR 版本字串，並傳回對應的偵錯工具介面。  
  
 [CoreClrDebugProcInfo 結構](coreclrdebugprocinfo-structure.md)  
 代表正在遠端電腦上執行的處理序。  
  
 [CoreClrDebugRuntimeInfo 結構](coreclrdebugruntimeinfo-structure.md)  
 代表載入遠端電腦上之處理序的 CLR 執行個體。  
  
 [GetStartupNotificationEvent 函式](getstartupnotificationevent-function.md)  
 建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。  
  
 [ICoreClrDebugTarget 介面](icoreclrdebugtarget-interface.md)  
 針對處理序和執行階段列舉，建立與遠端目標的連接。  
  
 [InitDbgTransportManager 函式](initdbgtransportmanager-function.md)  
 針對處理序和執行階段列舉，初始化要與遠端目標連接的傳輸管理員。  
  
 [ShutdownDbgTransportManager 函式](shutdowndbgtransportmanager-function.md)  
 關閉要與遠端目標電腦連接的傳輸管理員。  
  
## <a name="see-also"></a>請參閱

- [偵錯 Coclass](debugging-coclasses.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯全域靜態函式](debugging-global-static-functions.md)
- [偵錯列舉](debugging-enumerations.md)
- [偵錯結構](debugging-structures.md)
