---
title: ICorDebugBlockingObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778006"
---
# <a name="icordebugblockingobjectenum-interface"></a>ICorDebugBlockingObjectEnum 介面
提供[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構清單的列舉值。 這個介面是 ICorDebugEnum 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Next 方法](icordebugblockingobjectenum-next-method.md)|列舉[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的清單。|  
  
## <a name="remarks"></a>備註  
 每個 `CorDebugBlockingObject` 結構各代表一個封鎖執行緒的物件。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
