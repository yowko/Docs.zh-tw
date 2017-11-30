---
title: "ImportFile2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a>ImportFile2 方法
匯入組件和未繫結的模組。 這個方法就像[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pszFilename`  
 要匯入檔案的名稱。  
  
 `pszTargetName`  
 可用來重新命名檔案，因為它會連結至組件的選擇性的輸出檔名稱。  
  
 `pAssemblyScopeIn`  
 選擇性的範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。  
  
 `fSmartImport`  
 如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。  
  
 `pImportToken`  
 接收檔案或組件的 ID。  
  
 `ppAssemblyScope`  
 接收[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。 如果檔案不是組件，則為 NULL。  
  
 `pdwCountOfScopes`  
 會接收找到檔案及/或匯入的範圍。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>另請參閱  
 [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
