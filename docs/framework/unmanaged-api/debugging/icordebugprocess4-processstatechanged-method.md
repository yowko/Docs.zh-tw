---
title: ICorDebugProcess4：:Process狀態更改方法
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178634"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4：:Process狀態更改方法

通知 ICorDebug 管道進程外調試器正在繼續執行調試器。

## <a name="syntax"></a>語法

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>參數

 `eChange`\
[在][CorDebugStateChange 計數](cordebugstatechange-enumeration.md)的成員，描述進程執行狀態的變化。

## <a name="remarks"></a>備註

提供的方法是介面的一`ICorDebugProcess4`部分，對應于虛擬方法表的第四個槽。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標題：** 沒有

 **庫：** 沒有

 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorDebugProcess4 介面](icordebugprocess4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
