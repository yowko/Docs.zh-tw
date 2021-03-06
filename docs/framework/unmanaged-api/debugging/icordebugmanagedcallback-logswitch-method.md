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
ms.openlocfilehash: db6ccd63bbeadd7dcff1c7f8491b59017d431d12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720694"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch 方法

通知偵錯工具，common language runtime (CLR) managed 執行緒已呼叫類別中的方法， <xref:System.Diagnostics.Switch> 以建立、修改或刪除偵錯工具/追蹤參數。  
  
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
 在ICorDebugAppDomain 物件的指標，代表包含建立、修改或刪除偵錯工具/追蹤參數之 managed 執行緒的應用程式域。  
  
 `pThread`  
 在代表 managed 執行緒之 ICorDebugThread 物件的指標。  
  
 `lLevel`  
 在值，指出寫入事件記錄檔的描述性訊息的嚴重性層級。  
  
 `ulReason`  
 在 [LogSwitchCallReason](logswitchcallreason-enumeration.md) 列舉的值，表示在偵錯工具/追蹤參數上執行的作業。  
  
 `pLogSwitchName`  
 在偵錯工具/追蹤參數名稱的指標。  
  
 `pParentName`  
 在偵錯工具/追蹤參數的父系名稱指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
