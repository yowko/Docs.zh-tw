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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175963"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps 方法
使用指定的中繼資料簽名獲取程式集引用的屬性集。  
  
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
 [在]表示`mdAssemblyRef`要獲取屬性的程式集引用的中繼資料權杖。  
  
 `ppbPublicKeyOrToken`  
 [出]指向公開金鑰或中繼資料權杖的指標。  
  
 `pcbPublicKeyOrToken`  
 [出]返回的公開金鑰或權杖中的位元組數。  
  
 `szName`  
 [出]程式集的簡單名稱。  
  
 `cchName`  
 [在]大字元的大小`szName`。  
  
 `pchName`  
 [出]指向 中實際返回的寬字元數的指標`szName`。  
  
 `pMetaData`  
 [出]指向包含組件中繼資料的裝配元資料結構的指標。  
  
 `ppbHashValue`  
 [出]指向雜湊值的指標。 這是使用 SHA-1 演算法引用的程式集`PublicKey`屬性的雜湊值，除非設置了[AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md)枚舉的 arfFullOriginator 標誌。  
  
 `pcbHashValue`  
 [出]返回的雜湊值中的寬字元數。  
  
 `pdwAssemblyRefFlags`  
 [出]指向用於描述應用於程式集的中繼資料的標誌的指標。 標誌值是一個或多個[CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)值的組合。  
  
## <a name="return-value"></a>傳回值  
 此方法如果成功，將返回S_OK;否則，它將返回 Winerror.h 標標頭檔中定義的錯誤代碼之一。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
