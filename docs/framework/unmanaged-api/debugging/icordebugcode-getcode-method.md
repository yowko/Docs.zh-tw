---
title: ICorDebugCode::GetCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: db24228de7e8c98fd97f890b1e408515172299b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125663"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode 方法
取得指定函式的所有程式碼，格式化為可進行反組譯。 這個方法已在 .NET Framework 版本2.0 中被取代。 請改用[ICorDebugCode2：： GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>參數  
 `startOffset`  
 在函數開頭的位移。  
  
 `endOffset`  
 在函數結尾的位移。  
  
 `cBufferAlloc`  
 在將傳回程序代碼之 `buffer` 陣列的大小。  
  
 `buffer`  
 脫銷將傳回程序代碼的陣列。  
  
 `pcBufferSize`  
 脫銷傳回的位元組數目。  
  
## <a name="remarks"></a>備註  
 如果函式的程式碼已分成多個區塊，則會以增加的原生位移順序串連它們。 不會檢查指令界限。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1.0  
  
## <a name="see-also"></a>請參閱

- [GetCodeChunks 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
