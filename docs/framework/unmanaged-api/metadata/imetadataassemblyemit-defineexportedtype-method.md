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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177873"
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
 [在]要匯出的類型的名稱。 對於通用語言運行時的版本 1.1，匯出類型的名稱必須與 類型中`TypeDef`給出的名稱完全符合。  
  
 `tkImplementation`  
 [在]指定匯出類型的實現位置的權杖。 有效值及其相關含義包括：  
  
- `mdFile`該類型在此程式集中的其他檔中實現。  
  
- `mdAssemblyRef`該類型在不同的程式集中實現。  
  
- `mdExportedTYpe`類型嵌套在某種其他類型中。  
  
- `mdFileNil`類型與清單位於同一檔中，不是巢狀型別。  
  
 `tkTypeDef`  
 [在]指定要匯出的類型的中繼資料的權杖。 此值在檔中實現該類型的`TypeDef`表中輸入，並且僅當該檔位於此程式集中時才相關。  
  
 `dwExportedTypeFlags`  
 [在][CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)枚舉值的位組合，用於定義匯出類型的屬性設置。  
  
 `pmdct`  
 [出]指向返回的中繼資料權杖的指標，指示匯出的類型。  
  
## <a name="remarks"></a>備註  
 必須`ExportedType`為此程式集公開的並且在包含清單的模組以外的模組中實現的每一種類型定義元資料結構。  
  
## <a name="requirements"></a>需求  
 **平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** 科爾赫  
  
 **庫：** 用作 MsCorEE.dll 中的資源  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
