---
title: ICorDebugManagedCallback::LogSwitch 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d7432771a7d8eee9cea10f883dd3bd91f5ffb74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761384"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch 方法
通用語言執行平台 (CLR) managed 執行緒已呼叫方法，偵錯工具會告知<xref:System.Diagnostics.Switch>類別來建立、 修改或刪除偵錯/追蹤參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>參數  
 `PAppDomain`  
 [in]表示包含建立、 修改或刪除偵錯/追蹤切換的 managed 的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。  
  
 `pThread`  
 [in]ICorDebugThread 物件，表示 managed 的執行緒指標。  
  
 `lLevel`  
 [in]值，指出已寫入事件記錄檔的描述訊息的嚴重性層級。  
  
 `ulReason`  
 [in]值為[LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)偵錯/追蹤交換器上的列舉，指出作業執行。  
  
 `pLogSwitchName`  
 [in]偵錯/追蹤參數的名稱指標。  
  
 `pParentName`  
 [in]偵錯/追蹤切換的父系名稱指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
