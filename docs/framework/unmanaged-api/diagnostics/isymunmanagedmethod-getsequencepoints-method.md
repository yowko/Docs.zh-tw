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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615140"
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
 在，其 `ULONG32` 接收、、、、 `offsets` `documents` `lines` `columns` `endLines` 和 `endColumns` 陣列的大小。  
  
 `pcPoints`  
 脫銷的指標 `ULONG32` ，接收包含序列點所需的緩衝區長度。  
  
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

- [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)
