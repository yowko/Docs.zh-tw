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
ms.openlocfilehash: 320b3ca55a60ec7751c88a246ab6ee90b6b6c4cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724347"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next 方法

取得指定數目的 [COR_HEAPOBJECT](cor-heapobject-structure.md) 實例，其中包含 managed 堆積上物件的相關資訊。  
  
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
 擴展指標的陣列，每個指標都會指向 [COR_HEAPOBJECT](cor-heapobject-structure.md) 物件，該物件會提供 managed 堆積上物件的相關資訊。  
  
 pceltFetched  
 擴展實際傳回的 [COR_HEAPOBJECT](cor-heapobject-structure.md) 物件數目的指標 `objects` 。 如果 `celt` 為 1，則這個值可能是 `null`。  
  
## <a name="remarks"></a>備註  

 `COR_HEAPOBJECT.type` 欄位是計算巢狀參考數目之 COM 介面的識別項。 這個參考必須由 `ICorDebugHeapEnum::Next` 的呼叫者釋放。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugHeapEnum 介面](icordebugheapenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
