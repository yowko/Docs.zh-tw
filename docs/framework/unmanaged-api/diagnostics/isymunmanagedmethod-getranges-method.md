---
title: "ISymUnmanagedMethod::GetRanges 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRanges
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71d24bc83d6a26c800d0d97e885b322cc2b4ccbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges 方法
指定的文件中的位置，傳回陣列的開始和結束位移組對應的 Microsoft 中繼語言 (MSIL) 這個方法內的位置所涵蓋的範圍。 陣列是整數的陣列，而且 [開始、 結束、 開始、 結束] 的格式。 範圍組數目長度除以 2 的陣列。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a>參數  
 `document`  
 [in]要求位移的文件。  
  
 `line`  
 [in]對應到範圍的文件行。  
  
 `column`  
 [in]文件資料行對應到範圍。  
  
 `cRanges`  
 [in] `ranges` 陣列的大小。  
  
 `pcRanges`  
 [out]指標`ULONG32`包含範圍所需的緩衝區大小。  
  
 `ranges`  
 [out]接收範圍緩衝區的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
