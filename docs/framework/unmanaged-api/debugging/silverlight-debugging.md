---
title: Silverlight 偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414526d498b39e894c6bd3530a446f8c06f46378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572743"
---
# <a name="silverlight-debugging"></a>Silverlight 偵錯
本節中的主題說明 Common Language Runtime (CLR) 為了支援對 Windows 作業系統或 Macintosh 平台上執行的 Silverlight 應用程式進行偵錯，所提供的環境和介面。  
  
## <a name="in-this-section"></a>本節內容  
 [EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 提供在處理程序中列舉 CLRs 的機制。  
  
 [CloseCLREnumeration 函式](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 關閉所傳回的控制代碼陣列中任何有效 CLR 繼續-啟動事件[EnumerateCLRs 函式](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)，並釋放用於控制代碼和字串路徑陣列的記憶體。  
  
 [CreateCoreClrDebugTarget 函式](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 針對處理序和執行階段列舉，建立與遠端目標的連接。  
  
 [CreateCordbObject 函式](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 建立偵錯工具介面，以提供在遠端處理序上具現化 Managed 偵錯工作階段的功能。  
  
 [CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 從目標處理序中的 CLR 路徑來建立版本字串。  
  
 [CreateDebuggingInterfaceFromVersion 函式](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 接受從傳回的 CLR 版本字串[CreateVersionStringFromModule 函式](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)函式，並傳回對應的偵錯工具介面。  
  
 [CoreClrDebugProcInfo 結構](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 代表正在遠端電腦上執行的處理序。  
  
 [CoreClrDebugRuntimeInfo 結構](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 代表載入遠端電腦上之處理序的 CLR 執行個體。  
  
 [GetStartupNotificationEvent 函式](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 建立或開啟任何載入指定目標處理序的 Common Language Runtime (CLR) 將對其發出信號的事件控制代碼。  
  
 [ICoreClrDebugTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 針對處理序和執行階段列舉，建立與遠端目標的連接。  
  
 [InitDbgTransportManager 函式](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 針對處理序和執行階段列舉，對要與遠端目標連接的傳輸管理員初始化。  
  
 [ShutdownDbgTransportManager 函式](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 關閉傳輸管理員，以便與遠端目標電腦連接。  
  
## <a name="see-also"></a>另請參閱
- [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
