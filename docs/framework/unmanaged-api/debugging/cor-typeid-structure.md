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
ms.openlocfilehash: 5eeb5aef7edaa23385190a309144e1477da741e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697437"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID 結構

包含類型識別項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`token1`|第一個 token。|  
|`token2`|第二個 token。|  
  
## <a name="remarks"></a>備註  

 此 `COR_TYPEID` 結構是由許多偵錯工具方法所傳回，這些方法提供要進行垃圾收集之物件的相關資訊。 然後，您可以將它當作引數傳遞給其他的偵錯工具，以提供該專案的其他相關資訊。 例如，藉由列舉 [ICorDebugHeapEnum](icordebugheapenum-interface.md) 物件，您可以取得個別 [COR_HEAPOBJECT](cor-heapobject-structure.md) 物件，這些物件代表 managed 堆積上的個別物件。 然後，您可以將此 `COR_TYPEID` 值從 `COR_HEAPOBJECT.type` 欄位傳遞到 [ICorDebugProcess5：： GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) 方法，以取得提供物件類型資訊的 ICorDebugType 物件。  
  
 物件應為 `COR_TYPEID` 不透明。 不應存取或操作其個別欄位。 其唯一用途是做為方法呼叫中的參數提供的識別碼， `out` 而且可以傳遞給其他方法以提供其他資訊。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
