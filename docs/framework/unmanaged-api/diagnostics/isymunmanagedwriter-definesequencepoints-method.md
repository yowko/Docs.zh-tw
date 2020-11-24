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
ms.openlocfilehash: af8beb1ec627b93faeb7329a03579319ca3880ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678320"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints 方法

在目前的方法內定義一組序列點。 每個起始行和開始資料行定義方法內語句的開始。 每個結束行和結束資料行都會定義方法內的語句結尾。 陣列應以位移的遞增順序排序。 位移一律會從方法的開頭測量（以位元組為單位）。  
  
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
 在要為其定義序列點的檔物件。  
  
 `spCount`  
 在， `ULONG32` 指出每個 `offsets` 、、 `lines` `columns` 、 `endLines` 和 `endColumns` 緩衝區的大小。  
  
 `offsets`  
 在從方法開頭測量之序列點的位移。  
  
 `lines`  
 在序列點的起始行號。  
  
 `columns`  
 在序列點的起始欄號。  
  
 `endLines`  
 在序列點的結束行號。 這是選擇性參數。  
  
 `endColumns`  
 在序列點的結束欄號。 這是選擇性參數。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
