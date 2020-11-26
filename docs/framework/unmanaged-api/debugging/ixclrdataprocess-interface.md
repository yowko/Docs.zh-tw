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
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245337"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess 介面

提供查詢進程相關資訊的方法。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                                                               | 描述                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetRuntimeNameByAddress](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | 取得指定位址的名稱。                                                               |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | `AppDomain`依其唯一識別碼取得進程中的。                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | 提供控制碼來列舉進程的模組。                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | 列舉此進程的模組。                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | 釋放模組列舉期間使用的內部反覆運算器所使用的資源。               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | 提供控制碼，以列舉 `AppDomain` 從指定位址開始的方法實例。 |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | 從位址位移開始，列舉這個進程的方法實例。                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | 釋放實例列舉期間使用的內部反覆運算器所使用的資源。             |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。 不過，它是衍生自的 COM 介面， `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` 可透過一般的 COM 機制取得 GUID。

## <a name="requirements"></a>規格需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。
**標頭：** 沒有  
連結 **庫：** 沒有  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
