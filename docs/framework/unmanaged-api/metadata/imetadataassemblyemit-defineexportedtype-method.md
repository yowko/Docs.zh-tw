---
title: IMetaDataAssemblyEmit::DefineExportedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4d143d8dd5391283736d0140e8f1ced1dec53e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775320"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType 方法
為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>參數  
 `szName`  
 [in]若要匯出的型別名稱。 1\.1 版的 common language runtime，匯出的型別名稱必須完全相符的名稱，`TypeDef`類型。  
  
 `tkImplementation`  
 [in]語彙基元，指定匯出的型別實作的位置。 有效的值和其相關聯的意義如下：  
  
- `mdFile` 類型被實作這個組件中另一個檔案中。  
  
- `mdAssemblyRef` 類型被實作不同的組件中。  
  
- `mdExportedTYpe` 類型被巢狀其他類型。  
  
- `mdFileNil` 型別是在相同的檔案與資訊清單，並不是巢狀型別。  
  
 `tkTypeDef`  
 [in]指定要匯出類型的中繼資料語彙基元。 在中，這個值輸入`TypeDef`實作的型別和該檔案位於這個組件時，才會相關的檔案中的資料表。  
  
 `dwExportedTypeFlags`  
 [in]位元組合[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)定義匯出的類型屬性設定的列舉值。  
  
 `pmdct`  
 [out]傳回的中繼資料語彙基元，表示匯出的類型指標。  
  
## <a name="remarks"></a>備註  
 `ExportedType`必須針對每種類型，由這個組件和實作不同於包含資訊清單模組中定義中繼資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **LIBRARY:** 做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
