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
ms.openlocfilehash: 46c8b3fb2c9e7c353f74ef589e21f2a61df618fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777321"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch 方法
通知偵錯工具，common language runtime （CLR） managed 執行緒已在 <xref:System.Diagnostics.Switch> 類別中呼叫方法，以建立、修改或刪除偵錯工具/追蹤參數。  
  
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
 在ICorDebugAppDomain 物件的指標，表示包含建立、修改或刪除偵錯工具/追蹤參數之 managed 執行緒的應用程式域。  
  
 `pThread`  
 在代表 managed 執行緒之 ICorDebugThread 物件的指標。  
  
 `lLevel`  
 在值，指出寫入事件記錄檔之描述性訊息的嚴重性層級。  
  
 `ulReason`  
 在[LogSwitchCallReason](logswitchcallreason-enumeration.md)列舉的值，表示在偵錯工具/追蹤參數上執行的作業。  
  
 `pLogSwitchName`  
 在調試/追蹤參數名稱的指標。  
  
 `pParentName`  
 在調試層和追蹤參數之父系名稱的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
