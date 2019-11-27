---
title: ImportFile 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: cda6d90865f8ad2b9d565f6a6378c35b03c65bf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446987"
---
# <a name="importfile-method"></a>ImportFile 方法
匯入元件和解除系結模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFilename`  
 要匯入之檔案的完整名稱。  
  
 `pszTargetName`  
 選擇性的輸出檔案名，可以在檔案連結至元件時用來重新命名檔案。  
  
 `fSmartImport`  
 若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。  
  
 `pImportToken`  
 標記的指標，其中將儲存唯一的檔案識別碼。 檔案可以是元件或檔案。  
  
 `ppAssemblyScope`  
 接收[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)的指標。 如果檔案不是元件，則可以是 Null。  
  
 `pdwCountOfScopes`  
 已匯入之檔案和/或範圍計數的指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
