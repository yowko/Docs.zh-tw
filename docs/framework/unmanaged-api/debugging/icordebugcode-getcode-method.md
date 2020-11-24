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
ms.openlocfilehash: 20eac75a1f1d13b6a30267d56ff66024725e6f33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674771"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode 方法

取得指定之函式的所有程式碼，並針對反組解碼進行格式化。 在 .NET Framework 版本2.0 中，此方法已被取代。 請改用 [ICorDebugCode2：： GetCodeChunks](icordebugcode2-getcodechunks-method.md) 。  
  
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
 在 `buffer` 將傳回程序代碼的陣列大小。  
  
 `buffer`  
 擴展將傳回程序代碼的陣列。  
  
 `pcBufferSize`  
 擴展傳回的位元組數目。  
  
## <a name="remarks"></a>備註  

 如果函式的程式碼已分割成多個區塊，則會串連這些區塊以增加原生位移的順序。 未檢查指令界限。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [GetCodeChunks 方法](icordebugcode2-getcodechunks-method.md)
