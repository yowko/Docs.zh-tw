---
title: "ISymUnmanagedWriter::DefineSequencePoints 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints 方法
在目前的方法內定義一組序列點。 每個起始行和起始資料行定義方法內的陳述式的開始。 每個結束行和結束資料行定義方法內的陳述式的結尾。 陣列的位移遞增順序排序。 永遠從開頭的方法，以位元組為單位測量位移。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>參數  
 `document`  
 [in]文件物件為其定義序列點。  
  
 `spCount`  
 [in]A `ULONG32` ，表示每個的大小`offsets`， `lines`， `columns`， `endLines`，和`endColumns`緩衝區。  
  
 `offsets`  
 [in]從方法開頭算起的序列點的位移。  
  
 `lines`  
 [in]序列點起始行號。  
  
 `columns`  
 [in]序列點的起始欄號。  
  
 `endLines`  
 [in]序列點結束行號。 這是選擇性參數。  
  
 `endColumns`  
 [in]序列點結束欄號。 這是選擇性參數。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
