---
title: ICorDebugProcess4::ProcessStateChanged 方法
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
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948797"
---
# <a name="icordebugprocess4processstatechanged-method"></a>ICorDebugProcess4::ProcessStateChanged 方法

通知 ICorDebug 管線外的處理序偵錯工具會繼續偵錯的項目執行。

## <a name="syntax"></a>語法

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>參數

 `eChange`\
[in]成員[CorDebugStateChange 列舉](cordebugstatechange-enumeration.md)描述處理程序的執行狀態變更。

## <a name="remarks"></a>備註

提供的方法是一部分`ICorDebugProcess4`介面，而對應的虛擬方法表的第四個插槽。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標頭：** None

 **LIBRARY:** None
 
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorDebugProcess4 介面](icordebugprocess4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)