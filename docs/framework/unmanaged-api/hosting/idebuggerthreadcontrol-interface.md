---
title: IDebuggerThreadControl 介面
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805282"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl 介面
提供方法，以通知主機有關偵錯工具的執行緒封鎖和解除封鎖。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger 方法](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|通知主機傳送此回呼的執行緒即將在偵錯工具中封鎖。|  
|[ReleaseAllRuntimeThreads 方法](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|通知主機偵錯工具即將釋放所有封鎖的執行緒。|  
|[StartBlockingForDebugger 方法](idebuggerthreadcontrol-startblockingfordebugger-method.md)|通知主機偵錯工具即將開始封鎖所有線程。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
