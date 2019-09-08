---
title: ImportFile2 方法
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a03fc24e5ef932d13c0d195f53c703cdd3ff45ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776933"
---
# <a name="importfile2-method"></a>ImportFile2 方法
匯入元件和解除系結模組。 這個方法就像[ImportFile 方法](importfile-method.md)，但即使匯入的檔案不存在於磁片上，也會運作。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFilename`  
 要匯入之檔案的名稱。  
  
 `pszTargetName`  
 選擇性的輸出檔案名，可以在檔案連結至元件時用來重新命名檔案。  
  
 `pAssemblyScopeIn`  
 選擇性範圍[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。  
  
 `fSmartImport`  
 若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。  
  
 `pImportToken`  
 接收檔案或元件的識別碼。  
  
 `ppAssemblyScope`  
 接收[IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md)介面。 如果檔案不是元件，則為 Null。  
  
 `pdwCountOfScopes`  
 接收已匯入的檔案和/或範圍的。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
