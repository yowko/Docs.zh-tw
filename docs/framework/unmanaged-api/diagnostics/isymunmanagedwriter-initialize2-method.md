---
title: ISymUnmanagedWriter::Initialize2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 93a96a5da3342f4beff611de1d448dc199dd39dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687126"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 方法

設定與這個寫入器相關聯的中繼資料發射器介面，並設定將用來寫入偵錯工具符號的輸出檔名稱。 此方法也可讓您將程式資料庫的最終位置設定 (PDB) 檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>參數  

 `emitter`  
 在中繼資料的發射器介面指標。  
  
 `tempfilename`  
 在的指標 `WCHAR` ，其中包含要對其寫入偵錯工具符號的檔案名。 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 在如果有指定，符號寫入器會將符號發出至 <xref:System.Runtime.InteropServices.ComTypes.IStream> 指定的，而不是在參數中指定的檔案 `filename` 。 `pIStream` 是選用參數。  
  
 `fFullBuild`  
 [in] `true` 如果這是完整重建， `false` 如果這是累加式編譯，則為。  
  
 `finalfilename`  
 在的指標，其 `WCHAR` 為 PDB 檔案最後位置的路徑字串。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。  
  
## <a name="requirements"></a>需求  

 **標頭：** CorSym .idl、CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [Initialize 方法](isymunmanagedwriter-initialize-method.md)
