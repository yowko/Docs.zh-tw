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
ms.openlocfilehash: 6b30218cc7373494870ec54a3196857fcc5c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689390"
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
 在要匯出之類型的名稱。 若為 common language runtime 的1.1 版，則匯出的類型名稱必須完全符合中為類型指定的名稱 `TypeDef` 。  
  
 `tkImplementation`  
 在指定所匯出型別執行位置的標記。 有效值及其相關聯的意義如下：  
  
- `mdFile` 此類型會在此元件內的不同檔案中執行。  
  
- `mdAssemblyRef` 此類型會在不同的元件中執行。  
  
- `mdExportedTYpe` 類型會在其他類型中嵌套。  
  
- `mdFileNil` 此類型與資訊清單位於相同的檔案中，而不是巢狀型別。  
  
 `tkTypeDef`  
 在中繼資料的標記，這個中繼資料會指定要匯出的型別。 此值會在執行類型的檔案中的 `TypeDef` 資料表中輸入，而且只有在該檔案位於此元件中時才會相關。  
  
 `dwExportedTypeFlags`  
 在 [CorTypeAttr](cortypeattr-enumeration.md) 列舉值的位元組合，這些值會定義匯出型別的屬性設定。  
  
 `pmdct`  
 擴展傳回之元資料標記的指標，指出匯出的型別。  
  
## <a name="remarks"></a>備註  

 您 `ExportedType` 必須為這個元件所公開的每個型別定義元資料結構，並且在包含資訊清單的模組以外的模組中執行。  
  
## <a name="requirements"></a>需求  

 **平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MsCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
