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
ms.openlocfilehash: 1553e616f60b4f05c06b6457d47454dfb4bc2eb7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614769"
---
# <a name="isymunmanagedwriterinitialize-method"></a>ISymUnmanagedWriter::Initialize 方法
設定此寫入器將與之關聯的中繼資料發射器介面，並設定要寫入偵錯工具符號的輸出檔名稱。  
  
 這個方法只能呼叫一次，而且必須在任何其他寫入器方法之前呼叫。 某些寫入器可能需要檔案名。 不過，您一律可以將檔案名傳遞給這個方法，而不會對不使用檔案名的寫入器產生負面影響。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a>參數  
 `emitter`  
 在中繼資料發射器介面的指標。  
  
 `filename`  
 在要在其中寫入調試符號的檔案名。 如果檔案名稱是指定給不使用檔案名稱的寫入器，則這個參數會被忽略。  
  
 `pIStream`  
 在如果指定，符號寫入器會將符號發出至指定的， <xref:System.Runtime.InteropServices.ComTypes.IStream> 而不是參數中指定的檔案 `filename` 。 `pIStream` 是選用參數。  
  
 `fFullBuild`  
 [in] `true`如果這是完整重建，則為，`false`如果這是累加式編譯，則為。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedWriter 介面](isymunmanagedwriter-interface.md)
- [Initialize2 方法](isymunmanagedwriter-initialize2-method.md)
