---
title: IXCLRDataMethodDefinition 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 708c681a98113a406249a360c2fc81087e5b97f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790430"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition 介面

提供查詢方法定義相關資訊的方法。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

下列方法是介面中可用的一些方法。

| 方法                                                                                                                          | 描述                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](ixclrdatamethoddefinition-startenuminstances-method.md) | 提供給定 `IXCLRDataAppDomain`的方法實例列舉的控制碼。 |
| [EnumInstance](ixclrdatamethoddefinition-enuminstance-method.md)             | 列舉這個方法定義的實例。                                         |
| [EndEnumInstances](ixclrdatamethoddefinition-endenuminstances-method.md)     | 釋放實例列舉期間所使用之內部反覆運算器所使用的資源。         |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` 可透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
