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
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790472"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface 介面

提供 helper 方法，以從 `SOS`存取資料。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                               | 描述                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](isosdacinterface-getmethoddescdata-method.md) | 取得給定 MethodDesc 指標的資料。 |
| [GetMethodDescPtrFromIP](isosdacinterface-getmethoddescptrfromip-method.md) | 抓取 MethodDesc 的指標，其對應的方法包含指定的原生指令位址。 |
| [GetModuleData](isosdacinterface-getmoduledata-method.md)| 提取對應至在指定位址載入之模組的資料。 |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` 可透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
