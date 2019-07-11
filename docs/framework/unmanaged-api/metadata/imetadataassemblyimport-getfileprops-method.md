---
title: IMetaDataAssemblyImport::GetFileProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f3883b0cd1b7aca6265b738eace483c81eb37b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760148"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps 方法
取得具有指定之中繼資料簽章檔案的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdf`  
 [in]`mdFile`中繼資料語彙基元，表示要為其取得屬性的檔案。  
  
 `szName`  
 [out]檔案的簡單名稱。  
  
 `cchName`  
 [in]大小，以寬字元為單位的`szName`。  
  
 `pchName`  
 [out]中實際傳回的寬字元數目`szName`。  
  
 `ppbHashValue`  
 [out]雜湊值的指標。 這是雜湊，並使用 sha-1 演算法，該檔案。  
  
 `pcbHashValue`  
 [out]在傳回的雜湊值的寬字元數目。  
  
 `pdwFileFlags`  
 [out]指標，描述套用至檔案的中繼資料的旗標。 旗標值是由一或多個組成[CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
