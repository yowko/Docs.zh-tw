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
ms.openlocfilehash: 38763e687c66dcb038a874c9c17cb0d67e547816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699348"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints 方法

取得此方法內的所有序列點。  
  
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
 在， `ULONG32` 接收 `offsets` 、 `documents` 、 `lines` 、、 `columns` `endLines` 和 `endColumns` 陣列的大小。  
  
 `pcPoints`  
 擴展的指標 `ULONG32` ，會接收包含序列點所需的緩衝區長度。  
  
 `offsets`  
 在要在其中儲存 Microsoft 中繼語言 (MSIL 的陣列，) 序列點之方法開頭的位移。  
  
 `documents`  
 在要在其中儲存序列點所在檔的陣列。  
  
 `lines`  
 在陣列，要在其中儲存序列點所在檔中的行。  
  
 `columns`  
 在陣列，要在其中儲存序列點所在檔中的資料行。  
  
 `endLines`  
 在順序點結束之檔中的行陣列。  
  
 `endColumns`  
 在順序點結束之檔中的資料行陣列。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)
