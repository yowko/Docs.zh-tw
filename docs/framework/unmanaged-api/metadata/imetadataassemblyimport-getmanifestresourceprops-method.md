---
title: IMetaDataAssemblyImport::GetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009024"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps 方法
取得具有指定之中繼資料簽章之資訊清單資源的屬性集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdmr`  
 在`mdManifestResource`Token，代表要取得其屬性的資源。  
  
 `szName`  
 脫銷資源的名稱。  
  
 `cchName`  
 在的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷中實際傳回的寬字元數指標 `szName` 。  
  
 `ptkImplementation`  
 脫銷`mdFile`標記或 `mdAssemblyRef` token 的指標，分別代表包含資源的檔案或元件。  
  
 `pdwOffset`  
 脫銷值的指標，指定檔案內資源開頭的位移。  
  
 `pdwResourceFlags`  
 脫銷旗標的指標，描述套用至資源的中繼資料。 旗標值是一個或多個[CorManifestResourceFlags](cormanifestresourceflags-enumeration.md)值的組合。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
