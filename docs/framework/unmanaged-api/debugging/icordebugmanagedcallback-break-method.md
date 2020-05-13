---
title: ICorDebugManagedCallback::Break 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212460"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break 方法

執行程式碼資料流程中的指令時，通知偵錯工具 <xref:System.Reflection.Emit.OpCodes.Break> 。

## <a name="syntax"></a>語法

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>參數

`pAppDomain`\
在ICorDebugAppDomain 物件的指標，表示包含中斷指令的應用程式域。

`thread`\
在ICorDebugThread 物件的指標，表示包含中斷指令的執行緒。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
