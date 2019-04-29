---
title: COR_TYPEID 結構
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609437"
---
# <a name="cortypeid-structure"></a>COR_TYPEID 結構
包含類型識別項。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`token1`|第一個語彙基元。|  
|`token2`|第二個語彙基元。|  
  
## <a name="remarks"></a>備註  
 `COR_TYPEID`結構由偵錯的方法，可提供資訊以進行記憶體回收的物件數目。 它接著會傳遞做為引數其他偵錯的方法，提供關於該項目的其他資訊。 例如，透過列舉[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)物件，您可以擷取個別[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)代表 managed 堆積上的個別物件的物件。 您可以傳遞`COR_TYPEID`值從`COR_HEAPOBJECT.type`欄位設為[ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)方法來擷取 ICorDebugType 物件，提供物件的型別資訊。  
  
 A`COR_TYPEID`物件是不透明。 其個別的欄位不應該存取或操作。 其唯一用途是做為識別項提供做為`out`中方法呼叫，並可中，參數會傳遞至其他方法，以提供其他資訊。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
