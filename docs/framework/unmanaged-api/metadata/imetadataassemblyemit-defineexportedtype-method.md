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
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432063"
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
 在要匯出之類型的名稱。 若是 common language runtime 的版本1.1，匯出類型的名稱必須完全符合類型的 `TypeDef` 中指定的名稱。  
  
 `tkImplementation`  
 在指定匯出類型的實作為位置的 token。 有效值和其相關意義如下：  
  
- `mdFile` 類型是在此元件內的不同檔案中執行。  
  
- `mdAssemblyRef` 類型是在不同的元件中執行。  
  
- `mdExportedTYpe` 類型會在其他類型內嵌套。  
  
- `mdFileNil` 類型與資訊清單位於相同的檔案中，而且不是嵌套的類型。  
  
 `tkTypeDef`  
 在中繼資料的 token，指定要匯出的類型。 這個值會在執行類型之檔案的 `TypeDef` 資料表中輸入，而且只有在該檔案位於此元件中時，才會相關。  
  
 `dwExportedTypeFlags`  
 在[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)列舉值的位元組合，這個組合會定義匯出類型的屬性設定。  
  
 `pmdct`  
 脫銷傳回之元資料標記的指標，表示匯出的類型。  
  
## <a name="remarks"></a>備註  
 您必須針對此元件所公開的每個類型定義 `ExportedType` 元資料結構，並在包含資訊清單的模組以外的模組中執行。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
