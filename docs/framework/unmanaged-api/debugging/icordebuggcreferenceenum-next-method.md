---
title: ICorDebugGCReferenceEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef4ced1abd5b37af204ab3511a7cf8259303e8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755558"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next 方法
取得指定的數目[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)包含會進行記憶體回收的物件的相關資訊的執行個體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 celt  
 [in]要擷取的根憑證數目。  
  
 根目錄  
 [out]指標的陣列，其中每一個指向[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件，表示要進行記憶體回收的物件的根。  
  
 pceltFetched  
 [out]指標的數目[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)物件中實際傳回`roots`。 如果 `celt` 為 1，則這個值可能是 `null`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugGCReferenceEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
