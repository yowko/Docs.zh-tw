---
title: ISymUnmanagedReader::GetDocumentVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615029"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion 方法
取得指定檔的指定版本。 檔版本從1開始，而且每次使用[UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md)方法更新檔時，都會遞增。 如果 `pbCurrent` 參數為 `true` ，則這是檔的最新版本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>參數  
 `pDoc`  
 在指定的檔。  
  
 `version`  
 脫銷接收指定檔之版本之變數的指標。  
  
 `pbCurrent`  
 脫銷`true`如果這是檔的最新版本，或 `false` 如果不是最新版本，則為所接收之變數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)
