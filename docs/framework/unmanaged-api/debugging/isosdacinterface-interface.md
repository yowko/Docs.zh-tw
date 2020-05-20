---
title: ISOSDacInterface 介面
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420964"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface 介面

提供 helper 方法，以存取來自的資料 `SOS` 。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                               | 描述                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | 取得給定 MethodDesc 指標的資料。 |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | 抓取 MethodDesc 的指標，其對應的方法包含指定的原生指令位址。 |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| 提取對應至在指定位址載入之模組的資料。 |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自的 COM 介面，其 `IUnknown` 具有 `436f00f2-b42a-4b9f-870c-e73db66ae930` 可透過一般 COM 機制取得的 GUID。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
