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
ms.openlocfilehash: 4b1e8cb1cf34bb1c5ade1353351aab953e2b734a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670087"
---
# <a name="ixclrdatamethoddefinition-interface"></a>IXCLRDataMethodDefinition 介面

提供方法來查詢方法定義的相關資訊。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

下列方法是一些在介面中可用的方法。

| 方法                                                                                                                          | 描述                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [StartEnumInstances](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-startenuminstances-method.md) | 提供的控制代碼的方法執行個體的列舉型別的指定`IXCLRDataAppDomain`。 |
| [EnumInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-enuminstance-method.md)             | 列舉的執行個體，這個方法定義。                                         |
| [EndEnumInstances](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-endenuminstances-method.md)     | 釋放執行個體列舉期間使用的內部迭代器所使用的資源。         |

## <a name="remarks"></a>備註

此介面的執行階段內，而且不會公開透過任何標頭或程式庫檔案。 不過，它是 COM 介面衍生自`IUnknown`含有 GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` ，可以透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** None  
**LIBRARY:** None  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
