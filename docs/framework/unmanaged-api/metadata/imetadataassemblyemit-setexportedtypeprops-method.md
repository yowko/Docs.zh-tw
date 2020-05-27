---
title: IMetaDataAssemblyEmit::SetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: fa4f1f57cb8fe1ca81bbad6438a88bb43c48e7bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008075"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps 方法
修改指定的 `ExportedType` 中繼資料結構。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `ct`  
 在元資料標記，指定 `ExportedType` 要修改的元資料結構。  
  
 `tkImplementation`  
 在類型 `File` 為、或的 token， `AssemblyRef` `ExportedType` 指定如何實作為此型別。  
  
 `tkTypeDef`  
 在程式 `TypeDef` 代碼檔案中參考的 token。  
  
 `dwExportedTypeFlags`  
 在值的位元組合，這個組合會指定類型的屬性。  
  
## <a name="remarks"></a>備註  
 若要建立 `ExportedType` 元資料結構，請使用[IMetaDataAssemblyEmit：:D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
