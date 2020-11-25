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
ms.openlocfilehash: 2e75b6322e40fe010e9e0a3412a99c0d3460afae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719355"
---
# <a name="imetadataemitdefinetypedef-method"></a>IMetaDataEmit::DefineTypeDef 方法

建立通用語言執行時間類型的類型定義，並取得該類型定義的元資料標記。  
  
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
 在Unicode 的型別名稱。  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` 屬性。 這是值的位元遮罩 `CoreTypeAttr` 。  
  
 `tkExtends`  
 在基類的 token。 它必須是 `mdTypeDef` 或 `mdTypeRef` 標記。  
  
 `rtkImplements`  
 在標記陣列，指定這個類別或介面所執行的介面。  
  
 `ptd`  
 擴展 `mdTypeDef` 指派的權杖。  
  
## <a name="remarks"></a>備註  

 中的旗標 `dwTypeDefFlags` 會指定所建立的型別是否為一般類型系統參考型別 (類別或介面) 或一般型別系統數值型別。  
  
 根據提供的參數而定，此方法也可能會 `mdInterfaceImpl` 針對此類型繼承或執行的每個介面建立記錄。 不過，這個方法不會傳回任何這些 `mdInterfaceImpl` 標記。 如果用戶端想要在稍後新增或修改 `mdInterfaceImpl` 權杖，則必須使用 `IMetaDataImport` 介面來列舉權杖。 如果您想要使用介面的 COM 語法 `[default]` ，您應該將預設介面提供為中的第一個專案 `rtkImplements` ; 在類別上設定的自訂屬性會指出該類別具有預設介面 (一律假設為類別) 的第一個 `mdInterfaceImpl` token。  
  
 陣列的每個元素都會 `rtkImplements` 保存 `mdTypeDef` 或 `mdTypeRef` 標記。 陣列中的最後一個元素必須是 `mdTokenNil` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
