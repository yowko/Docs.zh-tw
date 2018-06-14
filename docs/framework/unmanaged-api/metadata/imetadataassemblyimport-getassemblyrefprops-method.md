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
ms.openlocfilehash: 0810ba945c1ed5874dae79704362a399c7349604
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445818"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps 方法
取得與指定的中繼資料簽章的組件參考的屬性集。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `mdar`  
 [in]`mdAssemblyRef`代表要取得屬性的組件參考的中繼資料語彙基元。  
  
 `ppbPublicKeyOrToken`  
 [out]公開金鑰或中繼資料語彙基元的指標。  
  
 `pcbPublicKeyOrToken`  
 [out]在傳回的公開金鑰或語彙基元的位元組數目。  
  
 `szName`  
 [out]組件的簡單名稱。  
  
 `cchName`  
 [in]大小，以寬字元的`szName`。  
  
 `pchName`  
 [out]中實際傳回的寬字元數目的指標`szName`。  
  
 `pMetaData`  
 [out]ASSEMBLYMETADATA 結構，其中包含組件中繼資料指標。  
  
 `ppbHashValue`  
 [out]雜湊值的指標。 這是雜湊，並使用 sha-1 演算法的`PublicKey`屬性的參考，除非 arfFullOriginator 旗標之組件[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)列舉集合。  
  
 `pcbHashValue`  
 [out]傳回雜湊值中的寬字元數目。  
  
 `pdwAssemblyRefFlags`  
 [out]旗標，敘述套用至組件的中繼資料指標。 旗標值是一或多個組合[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回 S_OK，如果它成功。否則，它會傳回其中 Winerror.h 標頭檔中定義的錯誤碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
