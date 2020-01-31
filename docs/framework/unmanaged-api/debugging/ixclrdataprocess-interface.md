---
title: IXCLRDataProcess 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a5d707d61513b030e5968af28db3c2a606e4419b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790378"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess 介面

提供查詢處理常式相關資訊的方法。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                                                               | 描述                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | 依其唯一識別碼取得進程中的 `AppDomain`。                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | 提供列舉進程模組的控制碼。                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | 列舉此進程的模組。                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | 釋放模組列舉期間所使用之內部反覆運算器所使用的資源。               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | 提供控制碼，以列舉從指定位址開始 `AppDomain` 的方法實例。 |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | 從位址位移開始，列舉這個進程的方法實例。                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | 釋放實例列舉期間所使用之內部反覆運算器所使用的資源。             |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 可透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。   
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
