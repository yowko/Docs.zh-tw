---
title: ISymUnmanagedReader::GetDocuments 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
ms.openlocfilehash: b8a3a74888a3caae03da6f88a003bd277939ae59
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615042"
---
# <a name="isymunmanagedreadergetdocuments-method"></a>ISymUnmanagedReader::GetDocuments 方法
傳回符號存放區中定義之所有檔的陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a>參數  
 `cDocs`  
 [in] `pDocs` 陣列的大小。  
  
 `pcDocs`  
 脫銷接收陣列長度之變數的指標。  
  
 `pDocs`  
 脫銷接收檔陣列之變數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [ISymUnmanagedReader 介面](isymunmanagedreader-interface.md)
