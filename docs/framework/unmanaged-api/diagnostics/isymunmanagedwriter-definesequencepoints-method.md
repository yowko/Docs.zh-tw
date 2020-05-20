---
title: ISymUnmanagedWriter::DefineSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614795"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints 方法
在目前的方法內定義一組序列點。 每個起始行和起始欄都會定義方法內的語句開頭。 每個結尾行和結束資料行都會定義方法內的語句結尾。 陣列應該以遞增的位移順序排序。 一定會從方法的開頭來測量位移（以位元組為單位）。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>參數  
 `document`  
 在要定義序列點的檔物件。  
  
 `spCount`  
 在， `ULONG32` 表示每個 `offsets` 、 `lines` 、 `columns` 、 `endLines` 和 `endColumns` 緩衝區的大小。  
  
 `offsets`  
 在從方法開頭測量之序列點的位移。  
  
 `lines`  
 在序列點的起始行號。  
  
 `columns`  
 在序列點的起始欄號。  
  
 `endLines`  
 在序列點的結束行號。 此為選擇性參數。  
  
 `endColumns`  
 在序列點的結束欄號。 此為選擇性參數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
