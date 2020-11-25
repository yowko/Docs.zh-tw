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
ms.openlocfilehash: 59149e79e926a0b9a3e549e013bf178e54ddf6fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705172"
---
# <a name="importfileex2-method"></a>ImportFileEx2 方法

匯入元件和未系結的模組。 此方法就像 [ImportFile 方法](importfile-method.md)，但即使正在匯入的檔案不存在於磁片上也一樣。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 要匯入的檔案名。  
  
 `pszTargetName`  
 目的檔案名的選擇性名稱。  
  
 `pAssemblyScopeIn`  
 選擇性匯入範圍 [IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md) 介面。  
  
 `fSmartImport`  
 若為 TRUE，則會使用 ImportTypes，否則必須手動執行匯入。  
  
 `dwOpenFlags`  
 要傳遞至 [OpenScope 方法](../metadata/imetadatadispenser-openscope-method.md)的旗標。  
  
 `pImportToken`  
 接收元件或檔案的唯一識別碼。  
  
 `ppAssemblyScope`  
 接收元件匯入範圍 [IMetaDataAssemblyImport 介面](../metadata/imetadataassemblyimport-interface.md) 介面。 如果檔案不是元件，則可以是 Null。  
  
 `pdwCountOfScopes`  
 接收已匯入的檔案和（或）範圍數目。  
  
## <a name="return-value"></a>傳回值  

 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  

 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
