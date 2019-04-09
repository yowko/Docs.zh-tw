---
title: ImportFileEx2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 784e58e0c5c2329705671580d53763f2ac30f0b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201347"
---
# <a name="importfileex2-method"></a>ImportFileEx2 方法
匯入組件和未繫結的模組。 這個方法就像是[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)，但即使正在匯入的檔案不存在磁碟上的運作方式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszFilename`  
 要匯入的檔案名稱。  
  
 `pszTargetName`  
 選擇性的目標檔案名稱。  
  
 `pAssemblyScopeIn`  
 選擇性的匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。  
  
 `fSmartImport`  
 如果為 TRUE，會使用 ImportTypes，否則匯入必須手動執行。  
  
 `dwOpenFlags`  
 要傳遞至旗標[OpenScope 方法](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)。  
  
 `pImportToken`  
 接收的組件或檔案的唯一識別碼。  
  
 `ppAssemblyScope`  
 接收的組件匯入範圍[IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面。 如果檔案不是組件時，就可以是 NULL。  
  
 `pdwCountOfScopes`  
 接收檔案和/或匯入的範圍的數目。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則會傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink.h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink 介面](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
