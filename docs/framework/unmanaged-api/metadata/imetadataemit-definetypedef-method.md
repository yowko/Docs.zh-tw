---
title: IMetaDataEmit::DefineTypeDef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450223"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法
建立 common language runtime 類型的類型定義，並取得該類型定義的元資料標記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>參數  
 `szTypeDef`  
 在Unicode 中的類型名稱。  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` 屬性。 這是 `CoreTypeAttr` 值的位元遮罩。  
  
 `tkExtends`  
 在基類的 token。 它必須是 `mdTypeDef` 或 `mdTypeRef` token。  
  
 `rtkImplements`  
 在Token 的陣列，指定此類別或介面所要執行的介面。  
  
 `ptd`  
 脫銷指派的 `mdTypeDef` token。  
  
## <a name="remarks"></a>備註  
 `dwTypeDefFlags` 中的旗標會指定所建立的型別是通用型別系統參考型別（類別或介面）還是一般型別系統實值型別。  
  
 視提供的參數而定，這個方法也可能會為這個類型所繼承或執行的每個介面建立 `mdInterfaceImpl` 記錄。 不過，這個方法不會傳回這些 `mdInterfaceImpl` token 中的任何一個。 如果用戶端想要在稍後新增或修改 `mdInterfaceImpl` token，它必須使用 `IMetaDataImport` 介面來列舉它們。 如果您想要使用 `[default]` 介面的 COM 語義，您應該提供預設介面做為 `rtkImplements`中的第一個元素。在類別上設定的自訂屬性會指出類別具有預設介面（一律假設為類別的第一個 `mdInterfaceImpl` token）。  
  
 `rtkImplements` 陣列的每個元素都會保留 `mdTypeDef` 或 `mdTypeRef` token。 陣列中的最後一個元素必須 `mdTokenNil`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
