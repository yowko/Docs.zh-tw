---
title: ICorDebugController::Continue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892857"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue 方法

呼叫[Stop 方法](icordebugcontroller-stop-method.md)之後，繼續執行 managed 執行緒。

## <a name="syntax"></a>語法

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>參數

`fIsOutOfBand`  
在如果從`true`頻外事件繼續，請將設為。否則，請將`false`設定為。

## <a name="remarks"></a>備註

`Continue`在呼叫`ICorDebugController::Stop`方法之後繼續處理。

執行混合模式的偵錯工具時，除非您`Continue`從頻外事件繼續，否則請勿在 Win32 事件執行緒上呼叫。

*內建事件*是 managed 事件或一般非受控事件，在此期間，偵錯工具支援與進程的受管理狀態互動。 在此情況下，偵錯工具會接收[ICorDebugUnmanagedCallback：:D ebugevent](icordebugunmanagedcallback-debugevent-method.md)回呼， `fOutOfBand`並將其`false`參數設定為。

*頻外事件*是一個不受管理的事件，在此情況下，當進程因事件而停止時，無法與處理常式的受管理狀態互動。 在此情況下，偵錯工具會`ICorDebugUnmanagedCallback::DebugEvent`接收回呼， `fOutOfBand`並將其`true`參數設定為。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
