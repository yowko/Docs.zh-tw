---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791359"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a>ICorDebugThread4::GetCurrentCustomDebuggerNotification 方法

取得目前線程上的目前[ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md)物件。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a>參數

`ppNotificationObject`\
脫銷目前線程上目前 `ICorDebugManagedCallback3::CustomNotification` 物件的指標。

## <a name="remarks"></a>備註

如果未從 `ICorDebugManagedCallback3::CustomNotification` 回呼中呼叫方法，或如果沒有目前的通知物件存在，則 `ppNotificationObject` 的值為 null。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>請參閱

- [ICorDebugThread4 介面](icordebugthread4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
