---
title: "IMetaDataAssemblyEmit::DefineExportedType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType 方法
為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>參數  
 `szName`  
 [in]若要匯出的類型名稱。 1.1 版的 common language runtime 所匯出的類型名稱必須完全符合指定的名稱為`TypeDef`類型。  
  
 `tkImplementation`  
 [in]指定匯出的類型，實作語彙基元。 有效的值和其相關聯的意義如下：  
  
-   `mdFile`類型會實作這個組件內不同的檔案。  
  
-   `mdAssemblyRef`類型是在不同的組件中的實作。  
  
-   `mdExportedTYpe`類型被巢狀其他型別。  
  
-   `mdFileNil`此類型是在相同的資訊清單檔案中，不是巢狀的類型。  
  
 `tkTypeDef`  
 [in]指定要匯出類型的中繼資料語彙基元。 在輸入此值`TypeDef`資料表中的檔案實作的型別，而且該檔案位於這個組件時，才會相關。  
  
 `dwExportedTypeFlags`  
 [in]位元組合[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)定義匯出的類型的屬性設定的列舉值。  
  
 `pmdct`  
 [out]指出所匯出的類型傳回的中繼資料語彙基元的指標。  
  
## <a name="remarks"></a>備註  
 `ExportedType`必須為這個組件由每個類型，它實作於以外含有資訊清單模組定義中繼資料結構。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor.h  
  
 **程式庫：**做為 MsCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMetaDataAssemblyEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
