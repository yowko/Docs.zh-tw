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
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610063"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 方法
設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。 此方法也可讓您設定程式資料庫（PDB）檔案的最終位置。  
  
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
 在中繼資料發射器介面的指標。  
  
 `tempfilename`  
 在的指標 `WCHAR` ，其中包含要對其寫入偵錯工具符號的檔案名。 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 在如果指定，符號寫入器會將符號發出至指定的， <xref:System.Runtime.InteropServices.ComTypes.IStream> 而不是在參數中指定的檔案 `filename` 。 `pIStream` 是選用參數。  
  
 `fFullBuild`  
 [in] `true`如果這是完整重建，則為，`false`如果這是累加式編譯，則為。  
  
 `finalfilename`  
 在的指標 `WCHAR` ，這是 PDB 檔案最後位置的路徑字串。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [Initialize 方法](isymunmanagedwriter-initialize-method.md)
