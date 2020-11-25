---
title: IMetaDataEmit::DefineNestedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 99dc141cca0f911c8dd65645f6c22d950cc678d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719537"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType 方法

建立類型定義的中繼資料簽章、傳回 `mdTypeDef` 該類型的標記，並指定定義的類型是參數所參考之類型的成員 `tdEncloser` 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>參數  

 `szTypeDef`  
 在Unicode 的型別名稱。  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` 屬性。 這是值的位元遮罩 `CorTypeAttr` 。  
  
 `tkExtends`  
 在基類的 token。 這可能是 `mdTypeDef` 或 `mdTypeRef` 標記。  
  
 `rtkImplements`[]  
 在Token 的陣列，這個陣列會指定這個類別或介面所執行的介面。  
  
 `tdEncloser`  
 在封入類型的標記。 陣列的最後一個元素必須是 `mdTokenNil` 。  
  
 `ptd`  
 擴展 `mdTypeDef` 指派的權杖。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 當做 MSCorEE.dll 中的資源使用  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
