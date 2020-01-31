---
title: ICorDebugHeapEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782486"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next 方法
取得指定的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例數目，其中包含 managed 堆積上物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 celt  
 [in] 要擷取的物件數目。  
  
 還原  
 脫銷指標的陣列，其中每一個都會指向一個[COR_HEAPOBJECT](cor-heapobject-structure.md)物件，以提供 managed 堆積上物件的相關資訊。  
  
 pceltFetched  
 脫銷`objects`中實際傳回之[COR_HEAPOBJECT](cor-heapobject-structure.md)物件數目的指標。 如果 `celt` 為 1，則這個值可能是 `null`。  
  
## <a name="remarks"></a>備註  
 `COR_HEAPOBJECT.type` 欄位是計算巢狀參考數目之 COM 介面的識別項。 這個參考必須由 `ICorDebugHeapEnum::Next` 的呼叫者釋放。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
