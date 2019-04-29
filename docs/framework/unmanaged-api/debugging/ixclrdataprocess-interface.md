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
ms.openlocfilehash: ff74a7acb5cc84c177f083c19402cd78977aeab5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775241"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess 介面

提供方法來查詢處理序的相關資訊。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                                                               | 描述                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | 取得`AppDomain`依其唯一識別碼的處理序中。                                              |
| [StartEnumModules](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummodules-method.md)                                   | 提供列舉的處理程序的模組控制代碼。                                        |
| [EnumModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummodule-method.md)                                               | 列舉此程序的模組。                                                         |
| [EndEnumModules](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummodules-method.md)                                       | 釋出內部模組列舉期間使用的迭代器所使用的資源。               |
| [StartEnumMethodInstancesByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | 提供列舉的方法執行個體的控制代碼`AppDomain`指定位址開頭。 |
| [EnumMethodInstanceByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-enummethodinstancebyaddress-method.md)             | 列舉位址位移處開始此程序的方法執行的個體。                  |
| [EndEnumMethodInstancesByAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | 釋放執行個體列舉期間使用的內部迭代器所使用的資源。             |

## <a name="remarks"></a>備註

此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。 不過，它是 COM 介面衍生自`IUnknown`含有 GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` ，可以透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。   
**標頭：** None  
**LIBRARY:** None  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
