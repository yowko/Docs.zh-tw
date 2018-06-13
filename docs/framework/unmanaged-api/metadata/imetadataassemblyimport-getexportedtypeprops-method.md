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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c76e46c75680d9fc0ad70e94da288f0c6b5e5ee1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446316"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps 方法
取得具有指定的中繼資料簽章之匯出類型的屬性集。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `mdct`  
 [in]`mdExportedType`中繼資料語彙基元，代表所匯出的類型。  
  
 `szName`  
 [out]匯出的類型名稱。  
  
 `cchName`  
 [in]大小，以寬字元為單位的`szName`。  
  
 `pchName`  
 [out]中實際傳回的寬字元數目 `szName`  
  
 `ptkImplementation`  
 [out]`mdFile`， `mdAssemblyRef`，或`mdExportedType`包含或允許匯出的類型的屬性存取的中繼資料語彙基元。  
  
 `ptkTypeDef`  
 [out]指標`mdTypeDef`表示檔案中的類型語彙基元。  
  
 `pdwExportedTypeFlags`  
 [out]描述套用至匯出的型別中繼資料的旗標指標。 旗標值可以是一個或多個[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)值。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
