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
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178990"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode 方法
獲取指定函數的所有代碼，這些代碼為拆卸格式化。 此方法已在 .NET 框架版本 2.0 中棄用。 使用[ICorDebugCode2：：請改為獲取代碼塊](icordebugcode2-getcodechunks-method.md)。  
  
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
 [在]函數開頭的偏移量。  
  
 `endOffset`  
 [在]函數末尾的偏移量。  
  
 `cBufferAlloc`  
 [在]要將代碼返回到`buffer`的陣列的大小。  
  
 `buffer`  
 [出]將代碼返回到的陣列。  
  
 `pcBufferSize`  
 [出]返回的位元組數。  
  
## <a name="remarks"></a>備註  
 如果函數的代碼已劃分為多個區塊，則它們按增加本機偏移的順序串聯。 未檢查指令邊界。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：** 1.1， 1.0  
  
## <a name="see-also"></a>另請參閱

- [GetCodeChunks 方法](icordebugcode2-getcodechunks-method.md)
