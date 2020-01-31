---
title: IXCLRDataModule 介面
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8757642db6c4375cf55d1f7288669c4c8a752a38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790398"
---
# <a name="ixclrdatamodule-interface"></a>IXCLRDataModule 介面

提供方法來查詢已載入模組的相關資訊。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>方法

| 方法                                                                                                                                | 描述                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [GetMethodDefinitionByToken](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | 取得對應至指定之元資料標記的方法定義。 |
| [要求](ixclrdatamodule-request-method.md)                                       | 要求填入模組資料所提供的緩衝區。       |
| [GetVersionId](ixclrdatamodule-getversionid-method.md)                             | 取得模組的版本識別碼。                                       |

## <a name="remarks"></a>備註

這個介面存在於執行時間內，而且不會透過任何標頭或程式庫檔案公開。 不過，它是衍生自 `IUnknown` 的 COM 介面，而 GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` 可透過一般的 COM 機制取得。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯介面](debugging-interfaces.md)
