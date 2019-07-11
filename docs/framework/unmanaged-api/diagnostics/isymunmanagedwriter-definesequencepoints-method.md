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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f07685351425a4685ac4a0c8e1b8e3c198b14187
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777306"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints 方法
在目前的方法內定義一組序列點。 每個起始行和起始資料行定義中方法的陳述式開頭。 每個結束行和結束資料行定義方法內的陳述式的結尾。 要以位移的遞增順序排序的陣列。 位移一律是從方法，以位元組為單位的開頭進行測量。  
  
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
 [in]文件物件，其定義序列點。  
  
 `spCount`  
 [in]A`ULONG32`表示的每個大小`offsets`， `lines`， `columns`， `endLines`，和`endColumns`緩衝區。  
  
 `offsets`  
 [in]從方法開頭進行測量之序列點的位移。  
  
 `lines`  
 [in]序列點的起始行號。  
  
 `columns`  
 [in]序列點的起始欄號。  
  
 `endLines`  
 [in]序列點結束的行號。 這個參數是選擇性的。  
  
 `endColumns`  
 [in]序列點結束欄號。 這個參數是選擇性的。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
