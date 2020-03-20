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
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178856"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next 方法
獲取包含有關託管堆上物件資訊的指定數量的[COR_HEAPOBJECT](cor-heapobject-structure.md)實例。  
  
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
  
 物件  
 [出]指標陣列，每個指標都[指向COR_HEAPOBJECT物件](cor-heapobject-structure.md)，該物件提供有關託管堆上的物件的資訊。  
  
 pceltFetched  
 [出]指向 中實際[返回COR_HEAPOBJECT物件的](cor-heapobject-structure.md)數量的指標`objects`。 如果 `celt` 為 1，則這個值可能是 `null`。  
  
## <a name="remarks"></a>備註  
 `COR_HEAPOBJECT.type` 欄位是計算巢狀參考數目之 COM 介面的識別項。 這個參考必須由 `ICorDebugHeapEnum::Next` 的呼叫者釋放。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
