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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893658"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode 方法
取得指定函式的所有程式碼，格式化為可進行反組譯。 這個方法已在 .NET Framework 版本2.0 中被取代。 請改用[ICorDebugCode2：： GetCodeChunks](icordebugcode2-getcodechunks-method.md) 。  
  
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
 在將傳回程序代碼`buffer`的陣列大小。  
  
 `buffer`  
 脫銷將傳回程序代碼的陣列。  
  
 `pcBufferSize`  
 脫銷傳回的位元組數目。  
  
## <a name="remarks"></a>備註  
 如果函式的程式碼已分成多個區塊，則會以增加的原生位移順序串連它們。 不會檢查指令界限。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [GetCodeChunks 方法](icordebugcode2-getcodechunks-method.md)
