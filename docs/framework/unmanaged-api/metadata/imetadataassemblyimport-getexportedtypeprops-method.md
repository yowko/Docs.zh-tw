---
title: IMetaDataAssemblyImport::GetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008400"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps 方法
取得具有指定的中繼資料簽章之已匯出類型的屬性集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `mdct`  
 在`mdExportedType`表示已匯出類型的元資料標記。  
  
 `szName`  
 脫銷匯出之類型的名稱。  
  
 `cchName`  
 在的大小（以寬字元為單位） `szName` 。  
  
 `pchName`  
 脫銷實際傳回的寬字元數`szName`  
  
 `ptkImplementation`  
 脫銷`mdFile`、 `mdAssemblyRef` 或 `mdExportedType` 元資料標記，其中包含或允許存取已匯出類型的屬性。  
  
 `ptkTypeDef`  
 脫銷`mdTypeDef`標記的指標，表示檔案中的類型。  
  
 `pdwExportedTypeFlags`  
 脫銷旗標的指標，描述套用至已匯出類型的中繼資料。 Flags 值可以是一或多個[CorTypeAttr](cortypeattr-enumeration.md)值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyImport 介面](imetadataassemblyimport-interface.md)
