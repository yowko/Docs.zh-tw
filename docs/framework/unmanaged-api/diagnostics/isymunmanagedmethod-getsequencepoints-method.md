---
title: ISymUnmanagedMethod::GetSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448884"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints 方法
取得這個方法內的所有序列點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>參數  
 `cPoints`  
 在`ULONG32`，會接收 `offsets`、`documents`、`lines`、`columns`、`endLines`和 `endColumns` 陣列的大小。  
  
 `pcPoints`  
 脫銷`ULONG32` 的指標，接收包含序列點所需的緩衝區長度。  
  
 `offsets`  
 在要在其中儲存序列點的方法開頭之 Microsoft 中繼語言（MSIL）位移的陣列。  
  
 `documents`  
 在要在其中儲存序列點所在檔的陣列。  
  
 `lines`  
 在要在其中儲存序列點所在檔中之行的陣列。  
  
 `columns`  
 在要在其中儲存序列點所在檔中之資料行的陣列。  
  
 `endLines`  
 在序列點結尾之檔中的行陣列。  
  
 `endColumns`  
 在序列點結尾之檔中的資料行陣列。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
