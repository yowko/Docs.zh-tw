---
title: ICorDebugProcess4 介面
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213578"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 介面

提供進程外執行控制的支援。

## <a name="methods"></a>方法

| 方法                                                                 | 描述                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | 通知 ICorDebug 管線，進程外偵錯工具正在繼續偵錯專案的執行。 |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `E930C679-78AF-4953-8AB7-B0AABF0F9F80` 可透過一般 COM 機制取得的 GUID。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** 無

連結**庫：** 無

**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
