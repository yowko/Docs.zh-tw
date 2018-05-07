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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54b0a02af7f22e775e3f9567de79664c9805b4e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="importfile-method"></a>ImportFile 方法
匯入組件和未繫結的模組。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>參數  
 `pszFilename`  
 要匯入檔案的完整限定的名稱。  
  
 `pszTargetName`  
 可用來重新命名檔案，因為它會連結至組件的選擇性的輸出檔名稱。  
  
 `fSmartImport`  
 如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。  
  
 `pImportToken`  
 語彙基元的唯一檔案識別碼的儲存位置的指標。 組件或檔案，可以是檔案。  
  
 `ppAssemblyScope`  
 接收指標[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)。 如果檔案不是組件時，就可以是 NULL。  
  
 `pdwCountOfScopes`  
 檔案及/或已匯入的範圍數目指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
