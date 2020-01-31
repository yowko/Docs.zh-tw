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
ms.openlocfilehash: 3a8e967a3ecc452ebda08872d8bcd9e9d08c766f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777697"
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next 方法
取得指定的[COR_GC_REFERENCE](cor-gc-reference-structure.md)實例數目，其中包含將被垃圾收集之物件的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 celt  
 在要抓取的根數目。  
  
 方根  
 脫銷指標陣列，其中每一個都會指向一個[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件，代表要進行垃圾收集之物件的根。  
  
 pceltFetched  
 脫銷`roots`中實際傳回之[COR_GC_REFERENCE](cor-gc-reference-structure.md)物件數目的指標。 如果 `celt` 為 1，則這個值可能是 `null`。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugGCReferenceEnum 介面](icordebuggcreferenceenum-interface.md)
- [偵錯介面](debugging-interfaces.md)
