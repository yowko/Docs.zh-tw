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
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009336"
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
 [in] `TypeDef`特性. 這是值的位元遮罩 `CoreTypeAttr` 。  
  
 `tkExtends`  
 在基類的 token。 它必須是 `mdTypeDef` 或 `mdTypeRef` 權杖。  
  
 `rtkImplements`  
 在Token 的陣列，指定此類別或介面所要執行的介面。  
  
 `ptd`  
 脫銷`mdTypeDef`指派的 token。  
  
## <a name="remarks"></a>備註  
 中的旗標 `dwTypeDefFlags` 會指定所建立的型別是通用型別系統參考型別（類別或介面）還是一般型別系統實值型別。  
  
 視提供的參數而定，這個方法也可能會 `mdInterfaceImpl` 為這個類型所繼承或執行的每個介面建立一筆記錄。 不過，這個方法不會傳回任何這些 `mdInterfaceImpl` 標記。 如果用戶端想要在稍後新增或修改 `mdInterfaceImpl` 權杖，它必須使用 `IMetaDataImport` 介面來加以列舉。 如果您想要使用介面的 COM 語義 `[default]` ，您應該提供預設介面做為中的第一個元素 `rtkImplements` ; 在類別上設定的自訂屬性會指出該類別具有預設介面（一律假設為類別的第一個 `mdInterfaceImpl` token）。  
  
 陣列的每個元素都 `rtkImplements` 包含 `mdTypeDef` 或 `mdTypeRef` token。 陣列中的最後一個元素必須是 `mdTokenNil` 。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結**庫：** 做為 Mscoree.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
