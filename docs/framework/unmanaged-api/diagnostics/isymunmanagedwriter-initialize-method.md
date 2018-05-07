---
title: ISymUnmanagedWriter::Initialize 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize 方法
設定與這個寫入器將會在相關的中繼資料發出器介面，並將偵錯符號寫入的輸出檔名稱。  
  
 一次，呼叫這個方法，它必須進行任何其他寫入器方法之前呼叫。 有些寫入器可能需要的檔案名稱。 不過，您一律可以檔案名稱傳遞至這個方法沒有任何未使用的檔案名稱的寫入器上的負面影響。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>參數  
 `emitter`  
 [in]中繼資料發出器介面指標。  
  
 `filename`  
 [in]偵錯符號寫入的檔案名稱。 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 [in]如果指定，符號寫入器會發出符號插入給定<xref:System.Runtime.InteropServices.ComTypes.IStream>，而不是檔案中指定`filename`參數。 `pIStream` 是選擇性參數。  
  
 `fFullBuild`  
 [in]`true`如果這是完整重建;`false`如果這是累加編譯。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：**於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize2 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
