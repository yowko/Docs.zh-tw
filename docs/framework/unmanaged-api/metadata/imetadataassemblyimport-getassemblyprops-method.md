---
title: IMetaDataAssemblyImport::GetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009050"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps 方法
取得具有指定之中繼資料簽章之元件的屬性集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mda`  
 [in]。 `mdAssembly`表示要取得屬性之元件的元資料標記。  
  
 `ppbPublicKey`  
 脫銷公用金鑰或元資料標記的指標。  
  
 `pcbPublicKey`  
 脫銷傳回的公開金鑰中的位元組數目。  
  
 `pulHashAlgId`  
 脫銷用來雜湊元件中之檔案的演算法指標。  
  
 `szName`  
 脫銷元件的簡單名稱。  
  
 `cchName`  
 在的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷中實際傳回的寬字元數 `szName` 。  
  
 `pMetaData`  
 脫銷包含元件中繼資料之 ASSEMBLYMETADATA 結構的指標。  
  
 `pdwAssemblyFlags`  
 脫銷描述套用至元件之中繼資料的旗標。 這個值是一個或多個[CorAssemblyFlags](corassemblyflags-enumeration.md)值的組合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
