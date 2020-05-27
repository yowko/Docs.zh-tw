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
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009063"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps 方法
取得具有指定的中繼資料簽章之元件參考的屬性集。  
  
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
 在`mdAssemblyRef`元資料標記，代表要取得其屬性的元件參考。  
  
 `ppbPublicKeyOrToken`  
 脫銷公用金鑰或元資料標記的指標。  
  
 `pcbPublicKeyOrToken`  
 脫銷傳回的公開金鑰或 token 中的位元組數目。  
  
 `szName`  
 脫銷元件的簡單名稱。  
  
 `cchName`  
 在的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷中實際傳回的寬字元數指標 `szName` 。  
  
 `pMetaData`  
 脫銷包含元件中繼資料之 ASSEMBLYMETADATA 結構的指標。  
  
 `ppbHashValue`  
 脫銷雜湊值的指標。 這是要參考之元件屬性的雜湊（使用 SHA-1 演算法） `PublicKey` ，除非已設定[AssemblyRefFlags](assemblyrefflags-enumeration.md)列舉的 arfFullOriginator 旗標。  
  
 `pcbHashValue`  
 脫銷傳回的雜湊值中的寬字元數。  
  
 `pdwAssemblyRefFlags`  
 脫銷旗標的指標，描述套用至元件的中繼資料。 旗標值是一個或多個[CorAssemblyFlags](corassemblyflags-enumeration.md)值的組合。  
  
## <a name="return-value"></a>傳回值  
 如果成功，這個方法會傳回 S_OK;否則，它會傳回 Winerror.h 標頭檔中所定義的其中一個錯誤碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
