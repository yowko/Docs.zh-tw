---
title: ICorDebugProcess4：:P rocessStateChanged 方法
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213565"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4：:P rocessStateChanged 方法

通知 ICorDebug 管線，進程外偵錯工具正在繼續偵錯專案的執行。

## <a name="syntax"></a>語法

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>參數

 `eChange`\
在[CorDebugStateChange 列舉](cordebugstatechange-enumeration.md)的成員，描述進程的執行狀態變更。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `ICorDebugProcess4` ，而且會對應至虛擬方法資料表的第四個插槽。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** 無

 連結**庫：** 無

 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>請參閱

- [ICorDebugProcess4 介面](icordebugprocess4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
