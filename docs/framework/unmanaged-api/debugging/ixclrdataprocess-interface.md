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
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178368"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess 介面

提供了查詢有關進程的資訊的方法。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                                                               | 描述                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | 通過進程`AppDomain`的唯一 ID 獲取 進程中的 。                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | 提供一個控制碼來枚舉進程的模組。                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | 枚舉此過程的模組。                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | 釋放模組枚舉期間使用的內部反覆運算器使用的資源。               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | 提供一個控制碼來枚舉從給定位址`AppDomain`開始的方法實例。 |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | 枚舉從位址偏移開始此過程的方法實例。                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | 釋放實例枚舉期間使用的內部反覆運算器使用的資源。             |

## <a name="remarks"></a>備註

此介面位於運行時內，不會通過任何標頭或庫檔公開。 但是，它是一個 COM 介面，派生自`IUnknown`GUID，`5c552ab6-fc09-4cb3-8e36-22fa03c798b7`可通過通常的 COM 機制獲得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。
**標題：** 沒有  
**庫：** 沒有  
**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
