---
title: IMetaDataAssemblyImport::GetAssemblyRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa633d554652050af51065e11221f898b34d5c63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772679"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps 方法
取得具有指定之中繼資料簽章的組件參考的屬性集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdar`  
 [in]`mdAssemblyRef`表示要為其取得屬性的組件參考的中繼資料語彙基元。  
  
 `ppbPublicKeyOrToken`  
 [out]公開金鑰或中繼資料語彙基元的指標。  
  
 `pcbPublicKeyOrToken`  
 [out]在傳回的公開金鑰或語彙基元的位元組數目。  
  
 `szName`  
 [out]組件的簡單名稱。  
  
 `cchName`  
 [in]大小，以寬字元為單位的`szName`。  
  
 `pchName`  
 [out]中實際傳回的寬字元數目的指標`szName`。  
  
 `pMetaData`  
 [out]ASSEMBLYMETADATA 結構，其中包含組件中繼資料指標。  
  
 `ppbHashValue`  
 [out]雜湊值的指標。 這是雜湊，並使用 sha-1 演算法`PublicKey`參考，除非 arfFullOriginator 旗標之組件的屬性[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列舉型別設定。  
  
 `pcbHashValue`  
 [out]在傳回的雜湊值的寬字元數目。  
  
 `pdwAssemblyRefFlags`  
 [out]指標，描述套用至組件的中繼資料的旗標。 旗標值是由一或多個組成[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回 S_OK，如果成功;否則，它會傳回一個在 Winerror.h 標頭檔中定義的錯誤碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
